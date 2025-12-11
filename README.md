# Expense Tracker Application

A full-stack expense tracking application built with Angular 20, .NET 9+, and SQL Server.

## Tech Stack

- **Frontend**: Angular 20
- **Backend**: .NET 9+ Web API
- **Database**: SQL Server

## Project Structure

```
EXPENSE TRACKER/
├── database/
│   └── schema.sql              # Database schema and sample data
├── ExpenseTracker.API/          # .NET 9+ Web API
│   ├── Controllers/            # API Controllers
│   ├── Data/                   # DbContext
│   ├── DTOs/                   # Data Transfer Objects
│   └── Models/                 # Entity Models
└── expense-tracker-frontend/    # Angular 20 Frontend
    └── src/
        └── app/
            ├── categories/     # Categories component
            ├── subcategories/  # Subcategories component
            ├── expenses/       # Expenses component
            ├── layout/         # Layout with sidebar
            └── services/       # API services
```

## Setup Instructions

### 1. Database Setup

1. Open SQL Server Management Studio (SSMS) or use sqlcmd
2. Create a new database:
   ```sql
   CREATE DATABASE ExpenseTracker;
   ```
3. Run the schema script:
   ```sql
   -- Execute the contents of database/schema.sql
   ```

Or use the connection string in `appsettings.json` to let Entity Framework create the database.

### 2. Backend Setup (.NET 9+ API)

1. Navigate to the API directory:
   ```bash
   cd ExpenseTracker.API
   ```

2. Update the connection string in `appsettings.json` if needed:
   ```json
   "ConnectionStrings": {
     "DefaultConnection": "Server=localhost;Database=ExpenseTracker;Trusted_Connection=True;TrustServerCertificate=True;"
   }
   ```

3. Restore packages and run:
   ```bash
   dotnet restore
   dotnet run
   ```

   The API will run on `https://localhost:5001` or `http://localhost:5000`

### 3. Frontend Setup (Angular 20)

1. Navigate to the frontend directory:
   ```bash
   cd expense-tracker-frontend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Update the API URL in services if your backend runs on a different port:
   - `src/app/services/category.service.ts`
   - `src/app/services/subcategory.service.ts`
   - `src/app/services/expense.service.ts`
   
   Change `http://localhost:5000` to match your API URL.

4. Run the development server:
   ```bash
   npm start
   ```

   The application will open at `http://localhost:4200`

## Features

### Manage Categories
- View all categories in a table
- Add new categories (Name, Description)
- Edit existing categories
- Delete categories with confirmation

### Manage Subcategories
- View all subcategories with their parent category
- Add new subcategories (Name, Description, Category dropdown)
- Edit existing subcategories
- Delete subcategories with confirmation

### Manage Expenses
- View all expenses with amount, date, category, and subcategory
- Add new expenses (Name, Description, Amount, Date, Category, Subcategory)
- Edit existing expenses
- Delete expenses with confirmation

## API Endpoints

### Categories
- `GET /api/categories` - Get all categories
- `GET /api/categories/{id}` - Get category by ID
- `POST /api/categories` - Create category
- `PUT /api/categories/{id}` - Update category
- `DELETE /api/categories/{id}` - Delete category

### Subcategories
- `GET /api/subcategories` - Get all subcategories
- `GET /api/subcategories/{id}` - Get subcategory by ID
- `POST /api/subcategories` - Create subcategory
- `PUT /api/subcategories/{id}` - Update subcategory
- `DELETE /api/subcategories/{id}` - Delete subcategory

### Expenses
- `GET /api/expenses` - Get all expenses
- `GET /api/expenses/{id}` - Get expense by ID
- `POST /api/expenses` - Create expense
- `PUT /api/expenses/{id}` - Update expense
- `DELETE /api/expenses/{id}` - Delete expense

## Notes

- The sidebar navigation is fixed on the left side
- All forms include validation
- Delete operations require confirmation
- The application uses CORS to allow the Angular app to communicate with the API
- Make sure both the API and Angular app are running simultaneously



