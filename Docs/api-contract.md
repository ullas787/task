# Task Manager — API Contract

**Version:** 1.0

## 1. Base URL

`http://localhost:5000`

## 2. Task data structure

| Field | Type | Description |
|---|---|---|
| id | UUID | Unique task identifier |
| title | String | Task description |
| is_completed | Boolean | Whether the task is completed |
| created_at | Timestamp | Task creation time |

## 3. API endpoints

### A. Get all tasks

- Method: `GET`
- Endpoint: `/api/tasks`
- Request body: None
- Success status: `200 OK`

Response:

```json
{
  "data": [
    {
      "id": "generated-uuid",
      "title": "Learn React",
      "is_completed": false,
      "created_at": "2026-11-15T14:00:00Z"
    }
  ]
}
```

### B. Create a task

- Method: `POST`
- Endpoint: `/api/tasks`
- Request body:

```json
{
  "title": "Learn API contracts"
}
```

- Success status: `201 Created`

Response:

```json
{
  "data": {
    "id": "generated-uuid",
    "title": "Learn API contracts",
    "is_completed": false,
    "created_at": "2026-11-15T14:00:00Z"
  }
}
```

### C. Update task completion

- Method: `PATCH`
- Endpoint: `/api/tasks/:id`
- Request body:

```json
{
  "is_completed": true
}
```

- Success status: `200 OK`

Response:

```json
{
  "data": {
    "id": "generated-uuid",
    "title": "Learn API contracts",
    "is_completed": true,
    "created_at": "2026-11-15T14:00:00Z"
  }
}
```

### D. Delete a task

- Method: `DELETE`
- Endpoint: `/api/tasks/:id`
- Request body: None
- Success status: `200 OK`

Response:

```json
{
  "message": "Task deleted successfully"
}
```

## 4. Error response format

All API errors should follow this structure:

```json
{
  "error": {
    "message": "Task not found"
  }
}
```

Common status codes:

- `400` — Invalid input
- `404` — Task not found
- `500` — Internal server error

## 5. Rules

1. Task titles cannot be empty.
2. The database generates task IDs.
3. New tasks start with `is_completed = false`.
4. The backend validates incoming requests.
5. All successful task responses use the agreed structure.