# 05. Database Design

## 5.1 Introduction

This chapter describes the database design of IssueFlow. It explains how data is organized, the major entities in the system, and the relationships between them.

IssueFlow uses a relational database to ensure data consistency, support complex relationships, and provide efficient data retrieval. PostgreSQL is used as the primary database, while Prisma ORM is used to simplify database access and schema management.

---

## 5.2 Database Overview

IssueFlow stores all application data in a PostgreSQL database.

The database is designed to support multiple organizations, configurable workflows, issue management, role-based access control, notifications, and audit logging. The structure follows a normalized relational model to minimize data redundancy while maintaining good performance.

The major categories of data include:

- Organization data
- User and authentication data
- Departments and teams
- Roles and permissions
- Workflow configuration
- Issues and issue history
- Comments and attachments
- Notifications
- Audit logs

---

## 5.3 Database Design Principles

The database design follows these principles:

- Relational database design
- Normalized data structure
- Referential integrity
- Multi-tenant support
- Scalability
- Data consistency
- Easy maintenance
- Extensible schema for future enhancements

---

## 5.4 Main Entities

The primary entities used in IssueFlow are listed below.

| Entity | Description |
|----------|-------------|
| Organization | Represents an organization using the platform. |
| Department | Represents departments within an organization. |
| Team | Represents teams inside departments. |
| User | Stores user information. |
| Role | Defines user roles. |
| Permission | Defines access permissions. |
| Workflow | Stores workflow definitions. |
| Workflow Stage | Represents workflow stages. |
| Workflow Transition | Defines allowed workflow transitions. |
| Issue | Stores issue information. |
| Comment | Stores comments on issues. |
| Attachment | Stores uploaded files. |
| Notification | Stores user notifications. |
| Audit Log | Stores important system activities. |

---

## 5.5 Entity Relationships

The major relationships between entities are:

- One organization can have many departments.
- One organization can have many users.
- One department can have many teams.
- One department can have many users.
- One team can have many users.
- One role can be assigned to many users.
- One workflow can contain multiple workflow stages.
- One workflow stage can have multiple workflow transitions.
- One workflow can be associated with many issues.
- One issue can have multiple comments.
- One issue can have multiple attachments.
- One user can create many issues.
- One user can receive many notifications.
- One user can generate many audit log entries.

---

## 5.6 Multi-Tenant Design

IssueFlow supports multiple organizations using a shared database model.

Each organization stores its own users, departments, workflows, issues, and related data while sharing the same database infrastructure. Most business entities are associated with an Organization to ensure logical separation of data.

This approach provides efficient resource utilization while maintaining isolation between organizations.

---

## 5.7 Naming Conventions

The following naming conventions are used throughout the database.

- Table names use PascalCase.
- Column names use camelCase.
- Primary keys use `id`.
- Foreign keys use `<entityName>Id`.
- Timestamp fields include:
  - `createdAt`
  - `updatedAt`
- Soft deletion uses:
  - `deletedAt`

These conventions ensure consistency across the database schema.

---

## 5.8 Data Integrity

Data integrity is maintained using:

- Primary keys
- Foreign keys
- Unique constraints
- Database transactions
- Validation at the application layer
- Referential integrity between related entities

These mechanisms help maintain accurate and consistent data throughout the system.

---

## 5.9 Entity Relationship Diagram

The Entity Relationship (ER) diagram illustrates the relationships between the major entities of IssueFlow.

> **Diagram:** `../diagrams/database/er-diagram.png`

---

## 5.10 Summary

The database design provides a structured foundation for IssueFlow. The relational model, combined with proper relationships, data integrity, and multi-tenant support, enables the application to manage workflow and issue data efficiently while remaining scalable and maintainable.