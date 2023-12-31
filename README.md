## extracker

A powerful API designed to facilitate the management and monitoring of user exercises. Leveraging the robustness of Node.js and the simplicity of Express, this API offers a seamless platform with endpoints for user registration, exercise addition, and exercise log retrieval. It enables users to easily register, log various exercises, and retrieve exercise history, providing a flexible and scalable solution for tracking and analyzing exercises.

[![js-standard-style](https://img.shields.io/badge/style-standard-brightgreen.svg?style=flat)](https://standardjs.com/) &nbsp;
[![Test](https://github.com/zhid0399123/extracker/actions/workflows/CI.yml/badge.svg)](https://github.com/zhid0399123/extracker/actions/workflows/CI.yml) &nbsp;
[![Deployment](https://github.com/zhid0399123/extracker/actions/workflows/fly.yml/badge.svg)](https://github.com/zhid0399123/extracker/actions/workflows/fly.yml) &nbsp;

## How It Works

### 1. Registration

Allows users to register by providing necessary information such as username and password. To register, issue a POST request to `https://extracker.fly.dev/v0/api/auth/register` with a JSON payload containing user credentials i.e `username` and `password`. The service will respond with the userId upon successful registration.

```bash
curl -X POST -H "Content-Type: application/json" -d '{"username": "newuser123", "password": "strongpassword"}' https://extracker.fly.dev/v0/api/auth/register
```

> Note: You can issue a HTTP POST request to `/authenticate` to get your `:userId` if forgotten.

```bash
curl -X POST -H "Content-Type: application/json" -d '{"username": "newuser123", "password": "strongpassword"}' https://extracker.fly.dev/v0/api/auth/authenticate
```

### 2. Adding User Exercises

To add exercise(s) make a HTTP `POST` request to `https://extracker.fly.dev/v0/api/users/:userId/exercises` where `:userId` is the unique user id provided after successful registration. The endpoint expect a JSON payload with `description`, `duration` in minutes and `date?` key properties.

```bash
curl -X POST -H "Content-Type: application/json" -d '{"description": "new exercise", "duration": "30"}' https://extracker.fly.dev/v0/api/users/1/exercises
```

### 3. Getting User Exercise

To retrieve user exercise, make a HTTP `GET` request to `https://extracker.fly.dev/v0/api/users/:userId/exercises/:exerciseId`. `:exerciseId` is the unidue id returned after successfully exercise creation operation.

```bash
curl -X GET https://extracker.fly.dev/v0/api/users/1/exercises/2
```

### 4. User Exercise Logs

To retrieve exercise logs for a specific user, make a HTTP `GET` request to `https://extracker.fly.dev/v0/api/users/:userId/logs?[from][&to][&limit]`. All the queries are optional.

```bash
curl -X GET https://extracker.fly.dev/v0/api/users/1/logs?from\=2023-12-01\&to\=2023-12-11\&limit\=4
```

## Contributing

Contributions are welcome! Feel free to open issues or submit pull requests. Please refer to the [Contributing Guidelines](CONTRIBUTING.md) to get started.

## License

This project is licensed under the MIT License. Refer to the [LICENSE](LICENSE) file for more details.
