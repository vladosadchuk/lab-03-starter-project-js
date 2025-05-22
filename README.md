# 📝 ToDo REST API

A simple task management REST API built with **Express.js** and **MongoDB**, containerized using **Docker** and **Docker Compose**.

---

## 📦 Features

- Create, list tasks
- MongoDB for persistent storage
- Express.js backend
- Dockerized application for easy local development and deployment

---

## 🗂 Project Structure

```
todo-app/
├── Dockerfile
├── docker-compose.yml
├── app.js
├── models/
│   └── Task.js
└── routes/
    └── tasks.js
```

## 🚀 Getting Started

### 🔧 Prerequisites

- [Docker](https://www.docker.com/products/docker-desktop)
- [Docker Compose](https://docs.docker.com/compose/)

---

### 🐳 Run with Docker Compose

```bash
docker-compose up --build
```

The application will start at:  
➡️ `http://localhost:3000/tasks`

---

### 📂 API Endpoints

| Method | Endpoint | Description       |
|--------|----------|-------------------|
| GET    | /tasks   | Get all tasks     |
| POST   | /tasks   | Create a new task |

#### POST `/tasks`

**Request body (JSON):**
```json
{
  "title": "Buy groceries"
}
```

---

## ✅ How to Test the API

### 🖥️ Option 1: Use `curl` (command line)

```bash
curl -X POST http://localhost:3000/tasks \
  -H "Content-Type: application/json" \
  -d '{"title": "Read a book"}'
```

Then verify:

```bash
curl http://localhost:3000/tasks
```

---

### 🌐 Option 2: Use the included `index.html` page

This project includes a simple HTML form for testing task creation.

➡️ Open [`index.html`](./index.html) in your browser  
➡️ Enter a task name and click "Send"  
➡️ Visit `http://localhost:3000/tasks` to see the result

> **Note:** CORS is enabled in the backend to allow requests from local HTML files.

---

## ⚙ Environment Variables

Environment variables are defined directly in `docker-compose.yml`:

```yaml
environment:
  - MONGO_URI=mongodb://mongo:27017/tododb
  - PORT=3000
```

If running manually (without Docker), create a `.env` file in the project root like this:

```env
MONGO_URI=mongodb://localhost:27017/tododb
PORT=3000
```

Then run:

```bash
npm install
npm start
```

---

---

## 🐘 Database Persistence

MongoDB uses a named volume `mongo-data` to persist data between container restarts:

```yaml
volumes:
  - mongo-data:/data/db
```

---
