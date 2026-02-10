# 🐾 VetCare Pro - Complete Veterinary Practice Management System

A comprehensive, production-ready veterinary clinic management system built with modern technologies.

## 📋 Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Environment Setup](#environment-setup)
- [Database Setup](#database-setup)
- [Running the Application](#running-the-application)
- [API Documentation](#api-documentation)
- [Deployment](#deployment)
- [License](#license)

## ✨ Features

### Core Modules

- **Master Data Management**
  - Pet Owner Registration with GDPR compliance
  - Pet Profile Management with photos, medical history
  - Weight tracking and growth charts
  - Microchip and tattoo ID tracking

- **Visit & Case Management**
  - Auto-generated case numbers
  - Chief complaint with severity tagging
  - Visit timeline and duration tracking
  - Linked follow-up visits

- **Clinical Examination**
  - Comprehensive vital parameters tracking
  - System-wise examination (cardiovascular, respiratory, neurological, etc.)
  - Auto-calculated status indicators
  - Historical trend analysis

- **Diagnostics & Tests**
  - Laboratory tests (CBC, LFT, KFT, serum electrolytes)
  - Imaging tests (X-ray, ultrasound, ECG, echocardiography)
  - Reference range validation
  - Critical value alerts

- **Diagnosis & Treatment**
  - Diagnosis with ICD-10 coding
  - Treatment plans with dosage calculator
  - Medication safety checks
  - Prescription PDF generation

- **Vaccination & Preventive Care**
  - Vaccination schedule by species/breed
  - Automatic due date calculation
  - Batch/lot number tracking
  - Certificate generation

- **Appointment Scheduling**
  - Calendar view (day/week/month)
  - Doctor availability management
  - Auto-reminder system
  - Conflict detection

- **Billing & Payments**
  - Itemized billing
  - Insurance integration
  - Payment tracking
  - PDF invoice generation

- **Inventory Management**
  - Stock level tracking
  - Expiry date alerts
  - Reorder level notifications
  - Purchase order generation

- **Automation & Notifications**
  - Multi-channel notifications (Email, SMS, WhatsApp, Push)
  - Vaccination reminders
  - Appointment reminders
  - Payment reminders

- **Analytics & Reporting**
  - Revenue analytics
  - Pet demographics
  - Common diagnoses
  - Doctor performance metrics

## 🚀 Tech Stack

### Backend
- **Framework**: NestJS (Node.js/TypeScript)
- **Database**: PostgreSQL 15+ with Prisma ORM
- **Authentication**: JWT with Passport.js
- **API Documentation**: Swagger/OpenAPI
- **Background Jobs**: BullMQ (Redis-based)
- **File Storage**: Cloudflare R2 (S3-compatible)
- **Notifications**: Twilio (SMS/WhatsApp), Resend (Email)

### Frontend
- **Framework**: Next.js 14 (React 18)
- **UI Library**: Tailwind CSS + shadcn/ui
- **State Management**: Zustand
- **Forms**: React Hook Form + Zod
- **Charts**: Recharts
- **Icons**: Lucide React

### Mobile (Coming Soon)
- **Framework**: Flutter 3.x
- **State Management**: Riverpod
- **Local Storage**: Hive
- **API Client**: Dio

### DevOps
- **Containerization**: Docker
- **CI/CD**: GitHub Actions
- **Hosting**: Railway/Render/Fly.io
- **Monitoring**: Sentry

## 📁 Project Structure

```
vetcare-pro/
├── backend/                    # NestJS Backend API
│   ├── prisma/
│   │   ├── schema.prisma      # Database schema
│   │   ├── migrations/        # Database migrations
│   │   └── seed.ts            # Seed data
│   ├── src/
│   │   ├── auth/              # Authentication module
│   │   ├── owners/            # Pet owners management
│   │   ├── pets/              # Pet profiles management
│   │   ├── visits/            # Visit & case management
│   │   ├── vitals/            # Clinical examination
│   │   ├── diagnostics/       # Lab tests & imaging
│   │   ├── treatment/         # Diagnosis & treatment plans
│   │   ├── vaccination/       # Vaccination management
│   │   ├── appointments/      # Appointment scheduling
│   │   ├── billing/           # Billing & invoices
│   │   ├── inventory/         # Inventory management
│   │   ├── notifications/     # Notification service
│   │   ├── analytics/         # Analytics & reports
│   │   ├── prisma/            # Prisma service
│   │   ├── app.module.ts      # Main app module
│   │   └── main.ts            # Entry point
│   ├── package.json
│   ├── tsconfig.json
│   └── .env.example
├── frontend/                   # Next.js Frontend
│   ├── app/
│   │   ├── (auth)/            # Authentication pages
│   │   ├── (dashboard)/       # Dashboard pages
│   │   │   ├── appointments/  # Appointments management
│   │   │   ├── pets/          # Pets management
│   │   │   ├── owners/        # Owners management
│   │   │   ├── visits/        # Visits management
│   │   │   ├── billing/       # Billing management
│   │   │   ├── inventory/     # Inventory management
│   │   │   └── analytics/     # Analytics & reports
│   │   ├── layout.tsx         # Root layout
│   │   ├── page.tsx           # Dashboard home
│   │   └── globals.css        # Global styles
│   ├── components/            # Reusable components
│   ├── lib/                   # Utilities & API client
│   ├── public/                # Static assets
│   ├── package.json
│   ├── next.config.js
│   └── tailwind.config.js
├── mobile/                     # Flutter Mobile App (Coming Soon)
│   ├── lib/
│   │   ├── features/
│   │   ├── core/
│   │   └── main.dart
│   └── pubspec.yaml
├── docs/                       # Documentation
│   ├── API.md                 # API documentation
│   ├── DATABASE.md            # Database schema docs
│   ├── DEPLOYMENT.md          # Deployment guide
│   └── USER_GUIDE.md          # User guide
├── docker-compose.yml         # Docker Compose configuration
├── .github/
│   └── workflows/
│       └── ci-cd.yml          # CI/CD pipeline
└── README.md                  # This file
```

## 🛠️ Getting Started

### Prerequisites

- Node.js 18+ and npm/yarn
- PostgreSQL 15+
- Redis (optional, for background jobs)
- Git

### Installation

1. **Clone the repository**

```bash
git clone https://github.com/yourusername/vetcare-pro.git
cd vetcare-pro
```

2. **Install backend dependencies**

```bash
cd backend
npm install
```

3. **Install frontend dependencies**

```bash
cd ../frontend
npm install
```

## 🔧 Environment Setup

### Backend Environment Variables

Create a `.env` file in the `backend` directory:

```bash
cp .env.example .env
```

Update the following variables:

```env
# Database
DATABASE_URL="postgresql://username:password@localhost:5432/vetcare_pro"

# JWT
JWT_SECRET="your-super-secret-jwt-key-change-this"
JWT_EXPIRES_IN="7d"

# Server
PORT=3000
NODE_ENV="development"

# File Storage (Cloudflare R2 or AWS S3)
R2_ACCOUNT_ID="your-cloudflare-account-id"
R2_ACCESS_KEY_ID="your-r2-access-key"
R2_SECRET_ACCESS_KEY="your-r2-secret-key"
R2_BUCKET_NAME="vetcare-pro"

# Redis (for background jobs)
REDIS_URL="redis://localhost:6379"

# Email (Resend)
RESEND_API_KEY="re_xxxxxxxxxxxxx"
EMAIL_FROM="noreply@vetcarepro.com"

# SMS (Twilio)
TWILIO_ACCOUNT_SID="ACxxxxxxxxxxxxx"
TWILIO_AUTH_TOKEN="your-twilio-auth-token"
TWILIO_PHONE_NUMBER="+1234567890"

# WhatsApp (Twilio)
WHATSAPP_FROM="whatsapp:+14155238886"

# Frontend URL
FRONTEND_URL="http://localhost:3001"
```

### Frontend Environment Variables

Create a `.env.local` file in the `frontend` directory:

```env
NEXT_PUBLIC_API_URL=http://localhost:3000/api/v1
```

## 💾 Database Setup

### 1. Create PostgreSQL Database

```bash
# Using psql
createdb vetcare_pro

# Or using SQL
psql -U postgres
CREATE DATABASE vetcare_pro;
\q
```

### 2. Run Prisma Migrations

```bash
cd backend
npx prisma migrate dev --name init
```

### 3. Seed Database (Optional)

```bash
npm run prisma:seed
```

### 4. Open Prisma Studio (Optional)

```bash
npx prisma studio
```

This will open a GUI at `http://localhost:5555` to view/edit data.

## 🚀 Running the Application

### Development Mode

**Terminal 1: Backend**
```bash
cd backend
npm run start:dev
```
Backend will run on `http://localhost:3000`
API Docs will be available at `http://localhost:3000/api/docs`

**Terminal 2: Frontend**
```bash
cd frontend
npm run dev
```
Frontend will run on `http://localhost:3001`

### Production Mode

**Backend**
```bash
cd backend
npm run build
npm run start:prod
```

**Frontend**
```bash
cd frontend
npm run build
npm run start
```

## 📚 API Documentation

Once the backend is running, visit:
- **Swagger UI**: `http://localhost:3000/api/docs`
- **OpenAPI JSON**: `http://localhost:3000/api-json`

### Example API Endpoints

**Authentication**
- `POST /api/v1/auth/register` - Register new user
- `POST /api/v1/auth/login` - Login user
- `GET /api/v1/auth/me` - Get current user profile

**Pets**
- `GET /api/v1/pets` - Get all pets
- `POST /api/v1/pets` - Register new pet
- `GET /api/v1/pets/:id` - Get pet by ID
- `PATCH /api/v1/pets/:id` - Update pet
- `GET /api/v1/pets/search?q=Max` - Search pets

**Visits**
- `GET /api/v1/visits` - Get all visits
- `POST /api/v1/visits` - Create new visit
- `GET /api/v1/visits/:id` - Get visit details

**Appointments**
- `GET /api/v1/appointments` - Get appointments
- `POST /api/v1/appointments` - Book appointment

## 🐳 Docker Deployment

### Using Docker Compose

```bash
# Start all services
docker-compose up -d

# View logs
docker-compose logs -f

# Stop all services
docker-compose down
```

### Manual Docker Build

**Backend**
```bash
cd backend
docker build -t vetcare-pro-backend .
docker run -p 3000:3000 --env-file .env vetcare-pro-backend
```

**Frontend**
```bash
cd frontend
docker build -t vetcare-pro-frontend .
docker run -p 3001:3000 vetcare-pro-frontend
```

## 🌐 Deployment

### Recommended Platforms

**Backend**
- Railway (Easy, free tier)
- Render (Good for small/medium apps)
- Fly.io (Global deployment)
- AWS/GCP/Azure (Enterprise)

**Frontend**
- Vercel (Recommended for Next.js)
- Netlify
- Cloudflare Pages

**Database**
- Supabase (PostgreSQL, free tier: 500MB)
- Neon (Serverless PostgreSQL)
- Railway PostgreSQL
- AWS RDS

### Environment-Specific Configuration

**Production Checklist**
- [ ] Change JWT_SECRET to a strong random string
- [ ] Enable HTTPS/SSL
- [ ] Set up proper CORS origins
- [ ] Configure rate limiting
- [ ] Set up monitoring (Sentry)
- [ ] Configure backup strategy
- [ ] Set up CI/CD pipeline
- [ ] Enable database connection pooling

## 📊 Cost Estimates

### Small Clinic (0-30 appointments/day)
- **Backend Hosting**: $0-10/month (Railway free tier or Render)
- **Database**: $0-25/month (Supabase free or paid)
- **Storage**: $0-5/month (Cloudflare R2)
- **Email/SMS**: $5-15/month
- **Total**: $10-55/month

### Medium Clinic (30-100 appointments/day)
- **Backend Hosting**: $20-50/month
- **Database**: $25-50/month
- **Storage**: $10-20/month
- **Email/SMS**: $20-50/month
- **Total**: $75-170/month

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Authors

- **Your Name** - *Initial work* - [YourGitHub](https://github.com/yourusername)

## 🙏 Acknowledgments

- NestJS for the amazing backend framework
- Next.js team for the frontend framework
- Prisma for the excellent ORM
- shadcn/ui for the beautiful UI components

## 📧 Support

For support, email support@vetcarepro.com or join our Discord server.

---

Made with ❤️ for veterinarians and their patients
