# IT Support Ticket Tracking System

A full-stack IT support ticket tracking application built with **Laravel**, **React.js**, and **Node.js**, featuring real-time analytics and comprehensive reporting.

## 🚀 Tech Stack

### Frontend
- **React.js** (TypeScript)
- **Vite** (Build tool)
- **Tailwind CSS** (Styling)
- **Recharts** (Charts & Analytics)
- **Lucide React** (Icons)

### Backend (Laravel)
- **Laravel 10** (PHP Framework)
- **Laravel Sanctum** (API Authentication)
- **MySQL** (Database)
- **Node.js** (Real-time features via Laravel Echo)

## 📋 Features

### 🔐 Authentication
- Secure login system with Laravel Sanctum
- Role-based access control (Admin, Support Agent)
- Session management
- Demo credentials included

### 📊 Dashboard
- Real-time ticket statistics
- Completion rate tracking
- Priority distribution
- Recent activity feed
- Interactive charts and graphs

### 🎫 Ticket Management
- Create, edit, and delete support tickets
- Track ticket status (Open, On Going, Pending, Done)
- Priority levels (RAB, THD, EBT)
- Filter and search functionality
- Export capabilities

### 📈 Analytics & Reports
- Comprehensive data visualization
- Tickets by company
- Priority breakdown
- Status overview
- Performance metrics
- Radar charts for multi-dimensional analysis

### ⚙️ Settings
- User profile management
- Notification preferences
- API configuration
- System integrations

## 🎨 UI/UX Features

- Modern, responsive design
- Clean and intuitive interface
- Color-coded status indicators
- Interactive data tables
- Modal forms for CRUD operations
- Real-time search and filtering

## 📦 Installation

### Frontend Setup

1. Install dependencies:
```bash
npm install
```

2. Start development server:
```bash
npm run dev
```

3. Build for production:
```bash
npm run build
```

### Backend Setup (Laravel)

1. Create a new Laravel project:
```bash
composer create-project laravel/laravel support-tracker-backend
```

2. Configure database in `.env`:
```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=support_tracker
DB_USERNAME=root
DB_PASSWORD=
```

3. Install Laravel Sanctum:
```bash
composer require laravel/sanctum
php artisan vendor:publish --provider="Laravel\Sanctum\SanctumServiceProvider"
```

4. Create migration for tickets table:
```bash
php artisan make:migration create_tickets_table
```

Migration schema:
```php
Schema::create('tickets', function (Blueprint $table) {
    $table->id();
    $table->date('date');
    $table->string('company');
    $table->text('concern');
    $table->string('anydesk_or_pc')->nullable();
    $table->enum('status', ['OPEN', 'ON GOING', 'PENDING', 'DONE']);
    $table->date('completion_date')->nullable();
    $table->text('remarks')->nullable();
    $table->string('communication')->nullable();
    $table->enum('priority', ['RAB', 'THD', 'EBT']);
    $table->timestamps();
});
```

5. Run migrations:
```bash
php artisan migrate
```

6. Create API routes in `routes/api.php`:
```php
Route::post('/login', [AuthController::class, 'login']);
Route::post('/logout', [AuthController::class, 'logout'])->middleware('auth:sanctum');

Route::middleware('auth:sanctum')->group(function () {
    Route::get('/tickets', [TicketController::class, 'index']);
    Route::post('/tickets', [TicketController::class, 'store']);
    Route::put('/tickets/{id}', [TicketController::class, 'update']);
    Route::delete('/tickets/{id}', [TicketController::class, 'destroy']);
});
```

7. Serve Laravel backend:
```bash
php artisan serve
```

## 🔑 Demo Credentials

### Admin Account
- **Email:** admin@company.com
- **Password:** admin123

### Support Agent Account
- **Email:** agent@company.com
- **Password:** agent123

## 📊 Data Structure

### Ticket Model
```typescript
interface Ticket {
  id: number;
  date: string;
  company: string;
  concern: string;
  anydeskOrPc: string;
  status: 'OPEN' | 'ON GOING' | 'PENDING' | 'DONE';
  completionDate: string;
  remarks: string;
  communication: string;
  priority: 'RAB' | 'THD' | 'EBT';
}
```

## 🎯 Priority Levels

- **RAB** - Critical/High Priority (Red)
- **THD** - Medium Priority (Purple)
- **EBT** - Low Priority (Orange)

## 📱 Responsive Design

The application is fully responsive and works seamlessly on:
- Desktop (1920px+)
- Laptop (1024px - 1919px)
- Tablet (768px - 1023px)
- Mobile (< 768px)

## 🔧 Current Implementation

This frontend application uses **localStorage** to simulate backend API calls. To connect to a real Laravel backend:

1. Update API base URL in `src/api.ts`
2. Configure CORS in Laravel
3. Set up Laravel Sanctum for authentication
4. Create corresponding Laravel controllers and models

## 📈 Future Enhancements

- Real-time notifications via Laravel Echo + Node.js
- File attachments for tickets
- Email notifications
- Advanced filtering and sorting
- Data export (CSV, PDF)
- Multi-language support
- Mobile app integration
- AI-powered ticket categorization

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is open-source and available under the MIT License.

---

Built with ❤️ using Laravel, React.js, and Node.js
