
# Microservices Project: User and Email Services

## Overview
This project consists of two microservices: `user-microservice` and `email-microservice`. The `user-microservice` handles user-related operations, while the `email-microservice` manages email functionalities. The services communicate asynchronously using RabbitMQ, and emails are sent via Gmail's SMTP server. Following the project of Michelli Brito on Youtube.

## Technologies Used
- **Java**: JDK 17
- **Spring Boot**: For building the microservices
- **Maven**: For dependency management
- **RabbitMQ**: For asynchronous communication (using CloudAMQP)
- **Gmail SMTP**: For sending emails

## Microservices

### User Microservice
Handles user management functionalitie of creating users.

#### Features:
- Asynchronous communication with the email service via RabbitMQ
- Persistence using JPA and PostgreSQL

### Email Microservice
Manages email sending functionalities.

#### Features:
- Listens for messages from RabbitMQ
- Sends emails using Gmail's SMTP server

## Getting Started

### Prerequisites
- Java 17
- Maven
- CloudAMQP account for RabbitMQ
- Gmail account for SMTP

### Installation

1. **Clone the repository:**
   \`\`\`bash
   git clone https://github.com/yourusername/microservices-project.git
   cd microservices-project
   \`\`\`

2. **Set up RabbitMQ:**
   - Sign up for a free account at [CloudAMQP](https://www.cloudamqp.com/)
   - Create a new instance and get the connection URL
   - Update the connection URL in \`application.properties\` for both microservices

3. **Configure Gmail SMTP:**
   - Enable "Less secure app access" on your Gmail account
   - Update \`application.properties\` in the \`email-microservice\` with your Gmail credentials

### Configuration

#### User Microservice (\`user-microservice/src/main/resources/application.properties\`):
\`\`\`properties
# Database Configuration
spring.datasource.url=jdbc:postgresql://localhost:5432/userdb
spring.datasource.username=yourusername
spring.datasource.password=yourpassword

# RabbitMQ Configuration
spring.rabbitmq.host=your-cloudamqp-url
spring.rabbitmq.username=your-username
spring.rabbitmq.password=your-password
\`\`\`

#### Email Microservice (\`email-microservice/src/main/resources/application.properties\`):
\`\`\`properties
# Database Configuration
spring.datasource.url=jdbc:postgresql://localhost:5432/userdb
spring.datasource.username=yourusername
spring.datasource.password=yourpassword

# RabbitMQ Configuration
spring.rabbitmq.host=your-cloudamqp-url
spring.rabbitmq.username=your-username
spring.rabbitmq.password=your-password

# Gmail SMTP Configuration
spring.mail.host=smtp.gmail.com
spring.mail.port=587
spring.mail.username=your-email@gmail.com
spring.mail.password=your-email-password
spring.mail.properties.mail.smtp.auth=true
spring.mail.properties.mail.smtp.starttls.enable=true
\`\`\`

### Running the Services

1. **Build the project with Maven:**
   \`\`\`bash
   mvn clean install
   \`\`\`

2. **Run User Microservice:**
   \`\`\`bash
   cd user-microservice
   mvn spring-boot:run
   \`\`\`

3. **Run Email Microservice:**
   \`\`\`bash
   cd email-microservice
   mvn spring-boot:run
   \`\`\`

## Future Work
- Implement complete CRUD for a RESTful API
- Implement additional user functionalities (e.g., password reset)
- Add more email templates and improve email customization
- Enhance security with OAuth2
- Set up CI/CD pipeline for automated testing and deployment

## Contributing
Feel free to fork this repository and contribute by submitting a pull request. Please ensure your changes are well-documented and tested.

## License
This project is licensed under the MIT License. See the \`LICENSE\` file for details.

---

Feel free to reach out with any questions or suggestions!
