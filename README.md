# Airbnb Clone Project
The Airbnb Clone Project is a comprehensive, real-world application designed to simulate the development of a robust booking platform like Airbnb. It involves a deep dive into full-stack development (Python Django, SQL, Redis, Docker, CI/CD), focusing on backend systems, database design, API development, and application security. This project fosters the understanding of complex architectures, workflows, and collaborative team dynamics while building a scalable web application.

# Team Roles
+ Backend Developer: Responsible for implementing API endpoints, database schemas, and business logic.
+ Database Administrator: Manages database design, indexing, and optimizations.
+ DevOps Engineer: Handles deployment, monitoring, and scaling of the backend services.
+ QA Engineer: Ensures the backend functionalities are thoroughly tested and meet quality standards.
+ Project Manager: Makes sure a product or its part is delivered on time and within budget

# Technology Stack
+ Django: A high-level Python web framework used for building the RESTful API.
+ Django REST Framework: Provides tools for creating and managing RESTful APIs.
+ PostgreSQL: A powerful relational database used for data storage.
+ GraphQL: Allows for flexible and efficient querying of data.
+ Celery: For handling asynchronous tasks such as sending notifications or processing payments.
+ Redis: Used for caching and session management.
+ Docker: Containerization tool for consistent development and deployment environments.
+ CI/CD Pipelines: Automated pipelines for testing and deploying code changes.

# Database Design
## The key entities required for the project
+ Users
    Represents: A person using the platform (guest or host). Key Fields:

    `id` (unique identifier),

    `name`,

    `email`,

    `password_hash`,

    `user_type` (e.g., "host" or "guest")

    Relationships:

    A user can own multiple properties (if a host). (1 - many)

    A user can make multiple bookings (if a guest). (1 - many)

    A user can write multiple reviews (1 - many)
    
+ Properties

    Represents: A listing / accomodation  available for rent. Key Fields:

    `id`,

    `owner_id` (references User),

    `title`,

    `description`,

    `location`,

    `price_per_night`

    Relationships:

    A property belongs to one user (the host). (1 - 1)

    A property can have many bookings. (1 - many)

    A property can have many reviews. (1 - many)

+ Bookings
    Represents: A reservation made by a user. Key Fields:

    `id`

    `property_id`

    `user_id` (the guest)

    `check_in_date`

    `check_out_date`

    `status` (e.g., "confirmed", "cancelled")

    Relationships:

    A booking is made by one user (the guest).  (Many -1)

    A booking is for one property. (1 -1)

    A booking may be linked to a payment.(1 -1)

+ Reviews
    Purpose: Feedback from guests about properties. Key Fields:

    `review_id` (Primary Key),

    `property_id`, 
    
    `guest_id` (Foreign Keys),

    `rating` (1–5),

    `comment`,

    `created_at`


    Relationships:

    A review is written by a guest for a property. (1 -1)

    A guest can leave one review per booking. (1 - 1)

+ Payments

    Purpose: Tracks transactions for bookings. Key Fields:

    `payment_id` (Primary Key),

    `booking_id` (Foreign Key → Bookings),

    `amount`, 

    `payment_method`, 
    
    `payment_status`,

    `paid_at`

    Relationships:

    A payment is linked to one booking. (1 - 1)