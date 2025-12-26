# em-project

Simple Spring Boot Employee REST API demo

## What this project does

This is a small Spring Boot application that exposes CRUD endpoints for `Employee` objects backed by JPA. The primary controller is `src/main/java/org/codingwallah/emproject/controller/EmpController.java`.

Available endpoints (base URL: `http://localhost:9090`)

- GET  /employees           -> list all employees (returns JSON array)
- GET  /employees/{id}      -> get single employee by id (returns JSON object)
- POST /employees           -> create new employee (accepts JSON body)
- PUT  /employees/{id}      -> update employee by id (accepts JSON body)
- DELETE /employees/{id}    -> delete employee by id


## Prerequisites

- Java 17 (project `pom.xml` sets `<java.version>17</java.version>`)
- Maven (optional if you use the included wrapper)
- (Optional) MySQL running locally if you want persistent storage using the provided `application.properties` settings. By default the project uses MySQL with the following properties (in `src/main/resources/application.properties`):

```
server.port=9090
spring.datasource.url=jdbc:mysql://localhost:3306/em-db?createDatabaseIfNotExist=true
spring.datasource.username=root
spring.datasource.password=rafid
spring.jpa.hibernate.ddl-auto=update
```

If you don't want to use MySQL, you can switch to the in-memory H2 DB by removing or commenting the MySQL properties and enabling H2 configuration, or add a profile for H2. The `pom.xml` already includes H2 as a runtime dependency.

## Run the application (Windows cmd.exe)

From the project root run:

```cmd
mvnw.cmd spring-boot:run
```

Or if you have Maven installed:

```cmd
mvn spring-boot:run
```

The app will start on port `9090` and the endpoints above will be available at `http://localhost:9090`.

## Example requests (Postman / cURL)

- List employees (GET):

    GET http://localhost:9090/employees

- Get one employee (GET):

    GET http://localhost:9090/employees/1

- Create employee (POST):

    POST http://localhost:9090/employees
    Headers:
      Content-Type: application/json

    Body (raw JSON):
    {
      "name": "Charlie",
      "phone": "555-1234",
      "email": "charlie@example.com"
    }

- Update employee (PUT):

    PUT http://localhost:9090/employees/1
    Headers:
      Content-Type: application/json

    Body (raw JSON):
    {
      "name": "Charlie Updated",
      "phone": "555-0000",
      "email": "charlie.updated@example.com"
    }

- Delete employee (DELETE):

    DELETE http://localhost:9090/employees/1
