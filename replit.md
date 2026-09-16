# Video Content Scheduler

Backend-first Spring Boot application for managing videos and their future publication schedules.

## Run & Operate

- `pnpm --filter @workspace/api-server run dev` — run the Spring Boot API server
- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `cd artifacts/api-server/java && mvn test` — run backend tests
- Required env: `DATABASE_URL` or `JDBC_DATABASE_URL` — PostgreSQL connection string

## Stack

- Java 21, Spring Boot, Maven
- API: Spring Web + Spring Validation
- DB: PostgreSQL + Spring Data JPA + Hibernate
- Migrations: Flyway
- API documentation: springdoc OpenAPI / Swagger UI

## Where things live

- `artifacts/api-server/java/src/main/java/com/example/videoscheduler/video` — Video domain, service, repository, and REST API
- `artifacts/api-server/java/src/main/resources/db/migration` — Flyway database migrations
- `artifacts/api-server/.replit-artifact/artifact.toml` — API service routing and health check

## Architecture decisions

- The first milestone is intentionally unauthenticated; ownership and roles arrive with the authentication phase.
- The service uses `/api` as its servlet context path so the existing artifact route remains stable.
- Public identifiers are UUIDs and response DTOs are kept separate from JPA entities.

## Product

The first milestone manages video metadata through a versioned REST API. Scheduling, publishing, retries, and authentication will be added as separate backend learning steps.

## User preferences

The project brief explicitly excludes a frontend and prioritizes backend depth.

## Gotchas

- Keep `DATABASE_URL` available when starting the API; Flyway runs migrations during application startup.

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details
