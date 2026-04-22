# User Management API

A simple ASP.NET Core Web API for managing users with middleware for logging, error handling, and authentication.

## Features

- CRUD operations for users
- Input validation
- Middleware for logging, authentication, and error handling
- JSON responses for all endpoints

## Prerequisites

- .NET 10.0 SDK
- Visual Studio Code or any IDE supporting .NET

## Installation

1. Clone or download the project.
2. Navigate to the project directory: cd UserManagementAPI
3. Restore dependencies: `dotnet restore`

## Running the Application

1. Build the project: `dotnet build`
2. Run the application: `dotnet run`
3. The API will be available at `http://localhost:5025`

## API Endpoints

All endpoints require `Authorization: Bearer valid-token` header.

### GET /api/users
Retrieves all users.

### GET /api/users/{id}
Retrieves a specific user by ID.

### POST /api/users
Creates a new user. Requires JSON body with name, email, department.

### PUT /api/users/{id}
Updates an existing user.

### DELETE /api/users/{id}
Deletes a user by ID.

## Testing

Use the requests.http file in VS Code with REST Client extension to test endpoints.

## Middleware

- **LoggingMiddleware**: Logs requests and responses.
- **ErrorHandlingMiddleware**: Catches exceptions and returns JSON errors.
- **AuthenticationMiddleware**: Validates Bearer tokens.

## Project Structure

- Models: Contains data models (User.cs)
- Middleware: Contains middleware classes
- Program.cs: Main application file
- requests.http: Test requests
 
## Request Examples (screenshots)

Screenshots showing how to run and inspect the API requests and responses are included in the `requestFig` folder. There are two sets:

- **POSTMAN**: screenshots showing requests and responses in Postman.
- **VSCODE**: screenshots showing requests and responses using the VS Code REST client and terminal output.

### Postman screenshots

![Postman 1](requestFig/POSTMAN/1.png)
![Postman 2](requestFig/POSTMAN/2.png)
![Postman 3](requestFig/POSTMAN/3.png)
![Postman 4](requestFig/POSTMAN/4.png)
![Postman 5](requestFig/POSTMAN/5.png)
![Postman 6](requestFig/POSTMAN/6.png)
![Postman 7](requestFig/POSTMAN/7.png)
![Postman 8](requestFig/POSTMAN/8.png)
![Postman 9](requestFig/POSTMAN/9.png)

### VS Code screenshots

![VSCode 1](requestFig/VSCODE/1.png)
![VSCode 2](requestFig/VSCODE/2.png)
![VSCode 3](requestFig/VSCODE/3.png)
![VSCode 4](requestFig/VSCODE/4.png)
![VSCode 5](requestFig/VSCODE/5.png)
![VSCode 6](requestFig/VSCODE/6.png)
![VSCode 7](requestFig/VSCODE/7.png)
![VSCode 8](requestFig/VSCODE/8.png)
![VSCode 9](requestFig/VSCODE/9.png)

## Compact gallery by request

This table maps each request from `requests.http` (1–9) to the endpoint tested, the result shown in the response, and links to the Postman / VS Code screenshots.

| Req | Endpoint (method) | Result shown | Postman | VS Code |
|---:|---|---|---:|---:|
| 1 | `GET /api/users` | 200 OK — list of users | ![P1](requestFig/POSTMAN/1.png) | ![V1](requestFig/VSCODE/1.png) |
| 2 | `GET /api/users/1` | 200 OK — single user | ![P2](requestFig/POSTMAN/2.png) | ![V2](requestFig/VSCODE/2.png) |
| 3 | `POST /api/users` | 201 Created — new user (id 4) | ![P3](requestFig/POSTMAN/3.png) | ![V3](requestFig/VSCODE/3.png) |
| 4 | `PUT /api/users/4` | 200 OK — update message | ![P4](requestFig/POSTMAN/4.png) | ![V4](requestFig/VSCODE/4.png) |
| 5 | `DELETE /api/users/4` | 200 OK — delete message | ![P5](requestFig/POSTMAN/5.png) | ![V5](requestFig/VSCODE/5.png) |
| 6 | `GET /api/users` (invalid token) | 401 Unauthorized | ![P6](requestFig/POSTMAN/6.png) | ![V6](requestFig/VSCODE/6.png) |
| 7 | `GET /api/users` (no token) | 401 Unauthorized | ![P7](requestFig/POSTMAN/7.png) | ![V7](requestFig/VSCODE/7.png) |
| 8 | `GET /api/nonexistent` | 404 Not Found — JSON error | ![P8](requestFig/POSTMAN/8.png) | ![V8](requestFig/VSCODE/8.png) |
| 9 | `POST /api/users` (invalid data) | 400 Bad Request — validation error | ![P9](requestFig/POSTMAN/9.png) | ![V9](requestFig/VSCODE/9.png) |

Notes:
- Thumbnails link to the images stored in `requestFig/POSTMAN` and `requestFig/VSCODE`.
- Use the `requests.http` file to reproduce each request; the README's examples follow that same numbering.