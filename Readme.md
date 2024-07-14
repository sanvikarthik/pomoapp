# Pomo - Pomodoro Timer API

![Python](https://skillicons.dev/icons?i=python)
![Django](https://skillicons.dev/icons?i=django)
![PostgreSQL](https://skillicons.dev/icons?i=postgres)
![Docker](https://skillicons.dev/icons?i=docker)

Pomo is a Pomodoro Timer API built with Django and Django REST framework. This API allows users to manage their Pomodoro sessions, tasks, and user profiles efficiently.

## Table of Contents
- [Features](#features)
- [Installation](#installation)
- [API Documentation](#api-documentation)
- [License](#license)

## Features
- User authentication and profile management
- CRUD operations for Pomodoro sessions
- Task management
- Docker support for easy deployment

## Installation

### Prerequisites
- Python 3.8+
- Docker (optional for containerized deployment)

### Local Setup

1. Clone the repository:
    ```sh
    git clone https://github.com/Himanshun3gi/pomo.git
    cd pomo
    ```

2. Create and activate a virtual environment:
    ```sh
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3. Install the dependencies:
    ```sh
    pip install -r requirements.txt
    ```

4. Apply the migrations:
    ```sh
    python manage.py migrate
    ```

5. Create a superuser to access the admin panel:
    ```sh
    python manage.py createsuperuser
    ```

6. Run the development server:
    ```sh
    python manage.py runserver
    ```

### Docker Setup

1. Build and run the Docker containers:
    ```sh
    docker-compose up --build
    ```

2. The application should now be running on `http://localhost:8000`.

## API Documentation

### Authentication

#### Register
- **URL:** `/api/register/`
- **Method:** `POST`
- **Body:**
  ```json
  {
    "username": "string",
    "password": "string",
    "email": "string"
  }
- **Response:**

```json
{
  "id": "integer",
  "username": "string",
  "email": "string"
}
```
### Login
**URL:** /api/login/
**Method:** POST
**Body:**

```json
{
  "username": "string",
  "password": "string"
}
```
**Response:**

```python
{
  "token": "string"
}
```
### Pomodoro Sessions
#### Create a Pomodoro Session
**URL:** /api/pomodoro-sessions/
**Method:** POST
**Headers:**

```console
Authorization: Token {token}
```
**Body:**

```json
{
  "task": "string",
  "duration": "integer"
}
```
**Response:**

```json
{
  "id": "integer",
  "task": "string",
  "duration": "integer",
  "user": "integer",
  "created_at": "datetime"
}
```
#### List Pomodoro Sessions
**URL:** /api/pomodoro-sessions/
**Method:** GET
**Headers:**

```console
Authorization: Token {token}
```
**Response:**
```json

[
  {
    "id": "integer",
    "task": "string",
    "duration": "integer",
    "user": "integer",
    "created_at": "datetime"
  }
]
```
#### Retrieve a Pomodoro Session
**URL:** /api/pomodoro-sessions/{id}/
**Method:** GET
**Headers:**

```console
Authorization: Token {token}
```
**Response:**

```json
{
  "id": "integer",
  "task": "string",
  "duration": "integer",
  "user": "integer",
  "created_at": "datetime"
}
```
#### Update a Pomodoro Session
**URL:** /api/pomodoro-sessions/{id}/
**Method:** PUT
**Headers:**

```console
Authorization: Token {token}
```
**Body:**

```json
{
  "task": "string",
  "duration": "integer"
}
```
**Response:**

```json
{
  "id": "integer",
  "task": "string",
  "duration": "integer",
  "user": "integer",
  "created_at": "datetime"
}
```
#### Delete a Pomodoro Session
**URL:** /api/pomodoro-sessions/{id}/
**Method:** DELETE
**Headers:**

```console
Authorization: Token {token}
```
**Response:** 204 No Content

### Tasks
#### Create a Task
**URL:** /api/tasks/
**Method:** POST
**Headers:**

```console
Authorization: Token {token}
```
**Body:**

```json
{
  "name": "string",
  "description": "string"
}
```
**Response:**

```json
{
  "id": "integer",
  "name": "string",
  "description": "string",
  "user": "integer",
  "created_at": "datetime"
}
```
#### List Tasks
**URL:** /api/tasks/
**Method:** GET
**Headers:**

```console
Authorization: Token {token}
```
**Response:**
```json

[
  {
    "id": "integer",
    "name": "string",
    "description": "string",
    "user": "integer",
    "created_at": "datetime"
  }
]
```
### Retrieve a Task
**URL:** /api/tasks/{id}/
**Method:** GET
**Headers:**

```console
Authorization: Token {token}
```
**Response:**

```json
{
  "id": "integer",
  "name": "string",
  "description": "string",
  "user": "integer",
  "created_at": "datetime"
}
```
### Update a Task
**URL:** /api/tasks/{id}/
**Method:** PUT
**Headers:**

```console
Authorization: Token {token}
```
**Body:**
```json

{
  "name": "string",
  "description": "string"
}
```
**Response:**

```json
{
  "id": "integer",
  "name": "string",
  "description": "string",
  "user": "integer",
  "created_at": "datetime"
}
```
### Delete a Task
**URL:** /api/tasks/{id}/
**Method:** DELETE
**Headers:**

```console
Authorization: Token {token}
```
**Response:** 204 No Content