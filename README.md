# Movie Ticket Booking Backend

A production-grade backend API for a Movie Ticket Booking Application built with Node.js, TypeScript, Express, and MongoDB.

## 🚀 Features

- **Authentication & Authorization**: JWT-based authentication with role-based access control
- **Movie Management**: CRUD operations for movies with search and filtering
- **Cinema Management**: Multi-screen cinema management with location tracking
- **Show Scheduling**: Flexible show scheduling with seat management
- **Ticket Booking**: Complete booking system with seat selection
- **Payment Integration**: Razorpay payment gateway integration
- **Email Notifications**: Automated email notifications for bookings
- **Image Upload**: Cloudinary integration for movie posters and user avatars
- **Review System**: User ratings and reviews for movies
- **API Documentation**: Comprehensive API endpoints with validation
- **Testing**: Jest testing setup with example tests
- **Security**: Rate limiting, CORS, helmet, and input validation
- **Logging**: Winston logging with file and console output

## 🛠️ Tech Stack

- **Runtime**: Node.js with TypeScript
- **Framework**: Express.js
- **Database**: MongoDB with Mongoose ODM
- **Authentication**: JWT (Access & Refresh tokens)
- **Password Hashing**: Bcrypt
- **Validation**: Zod schema validation
- **File Upload**: Multer + Cloudinary
- **Payment**: Razorpay integration
- **Email**: Nodemailer
- **Security**: Helmet, CORS, Rate limiting
- **Logging**: Winston
- **Testing**: Jest + Supertest
- **Containerization**: Docker

## 📁 Project Structure

```
src/
├── config/          # Database, cloudinary, Razorpay configs
├── constants/       # App-level constants & enums
├── controllers/     # Business logic per route
├── routes/          # Grouped by domain: auth, movie, booking, etc.
├── models/          # Mongoose schemas
├── middlewares/     # Error, auth, upload, validation
├── services/        # Payment, email, cloudinary logic
├── validators/      # Zod schemas for each route
├── utils/           # Token gen, response handler, logger
├── __tests__/       # Test files
├── app.ts           # Express app setup
└── server.ts        # Server entrypoint
```

## 🚀 Quick Start

### Prerequisites

- Node.js (v16 or higher)
- MongoDB (local or Atlas)
- npm or yarn

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd movie-ticket-booking-backend
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Environment Setup**
   ```bash
   cp .env.example .env
   ```
   
   Fill in your environment variables in `.env`:
   ```env
   NODE_ENV=development
   PORT=5000
   MONGODB_URI=mongodb://localhost:27017/movie-booking
   JWT_SECRET=your-super-secret-jwt-key
   JWT_REFRESH_SECRET=your-super-secret-refresh-key
   CLOUDINARY_CLOUD_NAME=your-cloud-name
   CLOUDINARY_API_KEY=your-api-key
   CLOUDINARY_API_SECRET=your-api-secret
   RAZORPAY_KEY_ID=your-razorpay-key-id
   RAZORPAY_KEY_SECRET=your-razorpay-secret
   EMAIL_HOST=smtp.gmail.com
   EMAIL_PORT=587
   EMAIL_USER=your-email@gmail.com
   EMAIL_PASS=your-app-password
   FRONTEND_URL=http://localhost:3000
   ```

4. **Start the development server**
   ```bash
   npm run dev
   ```

5. **Build for production**
   ```bash
   npm run build
   npm start
   ```

### Docker Setup

1. **Build the Docker image**
   ```bash
   docker build -t movie-booking-backend .
   ```

2. **Run the container**
   ```bash
   docker run -p 5000:5000 --env-file .env movie-booking-backend
   ```

## 📚 API Documentation

### Authentication Endpoints

#### Register User
```http
POST /api/auth/register
Content-Type: application/json

{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "SecurePass123",
  "phone": "1234567890"
}
```

#### Login User
```http
POST /api/auth/login
Content-Type: application/json

{
  "email": "john@example.com",
  "password": "SecurePass123"
}
```

#### Get Current User
```http
GET /api/auth/me
Authorization: Bearer <access_token>
```

### Movie Endpoints

#### Get All Movies
```http
GET /api/movies?page=1&limit=10&genre=action&search=avengers
```

#### Get Movie by ID
```http
GET /api/movies/:id
```

#### Create Movie (Admin Only)
```http
POST /api/movies
Authorization: Bearer <admin_token>
Content-Type: application/json

{
  "title": "Avengers: Endgame",
  "description": "After the devastating events of Avengers: Infinity War...",
  "genre": ["action", "adventure", "drama"],
  "cast": ["Robert Downey Jr.", "Chris Evans", "Mark Ruffalo"],
  "director": "Anthony Russo",
  "duration": 181,
  "language": "English",
  "releaseDate": "2019-04-26",
  "posterUrl": "https://example.com/poster.jpg"
}
```

### Health Check
```http
GET /api/health
```

## 🧪 Testing

### Run Tests
```bash
# Run all tests
npm test

# Run tests in watch mode
npm run test:watch

# Run tests with coverage
npm test -- --coverage
```

### Test Structure
- Unit tests for controllers
- Integration tests for API endpoints
- Database tests with isolated test database

## 🔧 Development

### Available Scripts

- `npm run dev` - Start development server with nodemon
- `npm run build` - Build TypeScript to JavaScript
- `npm start` - Start production server
- `npm test` - Run tests
- `npm run lint` - Run ESLint
- `npm run lint:fix` - Fix ESLint errors

### Code Style

- TypeScript with strict mode
- ESLint configuration
- Prettier formatting
- Consistent naming conventions

## 🔒 Security Features

- JWT token-based authentication
- Password hashing with bcrypt
- Rate limiting to prevent abuse
- CORS configuration
- Helmet for security headers
- Input validation with Zod
- SQL injection prevention (MongoDB)
- XSS protection

## 📊 Database Models

### User
- Authentication details
- Role-based access control
- Profile information
- Token management

### Movie
- Movie information
- Genre classification
- Cast and crew details
- Rating system

### Cinema
- Location information
- Screen management
- Amenities tracking

### Show
- Movie-cinema mapping
- Seat availability
- Pricing configuration

### Booking
- Ticket booking details
- Payment status
- Seat allocation

### Review
- User ratings
- Comments system
- Verification status

## 🚀 Deployment

### Environment Variables
Ensure all required environment variables are set in production:

- Database connection string
- JWT secrets
- Cloudinary credentials
- Razorpay keys
- Email configuration
- CORS origins

### Production Checklist
- [ ] Set NODE_ENV=production
- [ ] Configure MongoDB Atlas
- [ ] Set up Cloudinary account
- [ ] Configure Razorpay account
- [ ] Set up email service
- [ ] Configure CORS origins
- [ ] Set up logging
- [ ] Configure rate limiting
- [ ] Set up monitoring

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests for new functionality
5. Ensure all tests pass
6. Submit a pull request

## 📝 License

This project is licensed under the MIT License.

## 🆘 Support

For support and questions:
- Create an issue in the repository
- Check the API documentation
- Review the test examples

## 🔄 Roadmap

- [ ] Complete booking system implementation
- [ ] Add payment webhook handling
- [ ] Implement real-time seat updates
- [ ] Add admin dashboard endpoints
- [ ] Implement caching with Redis
- [ ] Add WebSocket support for real-time features
- [ ] Implement advanced search and filtering
- [ ] Add analytics and reporting endpoints # BookMyShowtime_backend
