FROM ubuntu:latest

WORKDIR /app

# Install Python and pip
RUN apt-get update && \
    apt-get install -y python3 python3-pip python3-venv && \
    apt-get clean

# Copy application files
COPY requirements.txt /app/
COPY devops /app/devops

# Create and use a virtual environment for Python
RUN python3 -m venv /app/venv && \
    /app/venv/bin/pip install --upgrade pip && \
    /app/venv/bin/pip install -r /app/requirements.txt

# Set environment variables to use the virtual environment
ENV PATH="/app/venv/bin:$PATH"

# Expose port (optional, based on your application)
EXPOSE 8000

# Run the application
ENTRYPOINT ["python3"]
CMD ["devops/manage.py", "runserver", "0.0.0.0:8000"]
