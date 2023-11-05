# Python Poetry Template
A template for python projects with poetry as package manager

## Usage
Click ``use this template`` button on the top right corner of this page and create your own repository. Then clone it to your local machine and change the project name and description in ``pyproject.toml``. 



## Installation
```	
pip install poetry
poetry install
```

## Docker
Here is a template dockerfile for your project:

Create a file named `Dockerfile` in the root of your project and paste the following code in it.

```dockerfile
FROM python:3.12-alpine

# change to any directory
WORKDIR /app
RUN pip install --upgrade pip

# set to your poetry version
RUN pip install poetry==1.7.0
RUN poetry config virtualenvs.create false

COPY pyproject.toml poetry.lock ./
RUN poetry install --no-interaction --no-ansi --only main

# COPY your project files
COPY python_template/ python_template/
COPY pytest.ini ./
COPY tests/ tests/

# set the ENTRYPOINT and/or CMD
CMD ["pytest"]
```	