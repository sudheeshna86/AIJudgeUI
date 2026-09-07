# AI Judge - Frontend

This is the **frontend application** for the **AI Judge Legal Case Management System**, built using **React.js (Vite)** and **Bootstrap 5**.

It provides a user-friendly interface for lawyers to create cases, manage arguments, and receive AI-powered verdicts.
**Live Link:**
https://judge-ui.vercel.app/
---

##  Features

### **Authentication**
- User registration and login using JWT tokens
- Persistent authentication using localStorage
- Protected routes accessible only to logged-in users
- Auto-redirect logged-in users to dashboard from landing page

### **Case Management**
- Create new legal cases with detailed information
- Join existing cases as Lawyer B
- View case details and status
- Track case progress through different stages

### **Document Upload**
- Upload documents via file upload
- Paste text directly into case
- Provide external document URLs
- Organize documents by side (A or B)

### **Argument Submission**
- Submit arguments during AI hearing
- Maximum 5 arguments per side
- Real-time argument counter and limits
- View all submitted arguments from both sides

### **AI Verdict Generation**
- Generate AI-powered verdicts based on case evidence
- Full-page loading spinner during verdict generation
- Display verdict with reasoning and confidence score
- Automatic winner detection

### **User Interface**
- Responsive design with Bootstrap 5
- Clean and professional layout
- Real-time status updates
- Side-by-side panel comparison (Side A vs Side B)
- Attractive landing page with gradient background

---

## 📁 Folder Structure

```
frontend/
├── public/                    # Static assets
├── src/
│   ├── api/
│   │   ├── client.js         # Axios HTTP client setup
│   │   ├── auth.js           # Authentication API calls
│   │   ├── cases.js          # Case CRUD operations
│   │   └── judge.js          # AI verdict and arguments
│   │
│   ├── components/
│   │   ├── Sidebar.jsx       # Navigation sidebar
│   │   ├── ProtectedRoute.jsx # Route protection wrapper
│   │   └── ...
│   │
│   ├── pages/
│   │   ├── Index.jsx         # Landing page (auto-redirect)
│   │   ├── Login.jsx         # User login page
│   │   ├── Register.jsx      # User registration page
│   │   ├── Dashboard.jsx     # Main dashboard
│   │   ├── CasesList.jsx     # View user's cases
│   │   ├── BrowseCases.jsx   # Browse and join cases
│   │   ├── CreateCase.jsx    # Create new case
│   │   ├── CaseDetails.jsx   # Case detail view with documents
│   │   ├── Hearing.jsx       # AI hearing and arguments
│   │   └── NotFound.jsx      # 404 page
│   │
│   ├── App.jsx               # Main app router
│   └── main.jsx              # Application entry point
│
├── .env                       # Environment variables
├── package.json              # Dependencies
├── vite.config.js            # Vite configuration
└── README.md                 # This file
```

---

##  Tech Stack

- **React.js (Vite)** – Fast frontend framework
- **React Router DOM** – Client-side routing
- **Axios** – HTTP requests and API communication
- **Bootstrap 5** – Responsive UI and styling
- **JWT** – Token-based authentication
- **localStorage** – Client-side data persistence

---

## Pages & Modules

### **Index / Landing Page**
- Display welcome message and features
- Show login and register buttons
- Auto-redirect logged-in users to dashboard

### **Authentication (Login/Register)**
- User registration with email and password
- Login with email and password
- Role selection (Lawyer A or Lawyer B)
- JWT token storage in localStorage

### **Dashboard**
- Overview of user's cases
- Quick access to active cases
- Statistics and case summary

### **Cases Management**
- **My Cases** – View all cases created by user
- **Browse Cases** – Find and join cases as Lawyer B
- **Create Case** – Form to create new legal case
- **Case Details** – View case information and documents

### **AI Hearing**
- Side A and Side B submission panels
- Document upload and text input
- Argument submission with real-time counter
- AI verdict generation with full-page spinner
- All arguments display (visible to both sides)
- Winner detection and case closure

---

##  Environment Setup

Create a `.env` file in the `frontend` directory:

```env
VITE_API_URL=http://localhost:5000/api
```
Live Link:
https://judge-ui.vercel.app/

For production:
```env
VITE_API_URL=https://judgebackend-75yd.onrender.com/api
```

---

##  Installation & Running

### Prerequisites
- Node.js v16+ and npm

### Install Dependencies
```bash
cd frontend
npm install
```

### Run Development Server
```bash
npm run dev
```
The app will run on: `http://localhost:5173`

### Build for Production
```bash
npm run build
```

### Preview Production Build
```bash
npm run preview
```

---

## 🔗 API Integration

The frontend connects to the backend API with the following main endpoints:

### **Authentication**
- `POST /api/auth/register` – Register new user
- `POST /api/auth/login` – Login and get JWT token

### **Cases**
- `GET /api/cases` – Get all cases
- `POST /api/cases` – Create new case
- `GET /api/cases/:id` – Get case details
- `PUT /api/cases/:id` – Update case
- `POST /api/cases/:id/join` – Join case as Lawyer B

### **Documents**
- `POST /api/cases/:id/documents` – Upload document
- `GET /api/cases/:id/documents` – Get case documents

### **Arguments & Verdict**
- `POST /api/arguments` – Submit argument
- `GET /api/arguments/:caseId` – Get all arguments
- `POST /api/verdict` – Generate AI verdict

---

## 👤 Test Accounts

| Email | Password | Role |
|-------|----------|------|
| honey@gmail.com | 123456 | Lawyer B |

---

##  User Flow

1. **Visit Landing Page** – Auto-redirects if logged in, shows login/register if not
2. **Register** – Create account with email, password, and role
3. **Login** – Sign in with credentials
4. **Dashboard** – View overview and available cases
5. **Create Case** – As Lawyer A, create a new case with details
6. **Join Case** – As Lawyer B, browse and join existing cases
7. **Upload Documents** – Both sides upload supporting documents
8. **Submit Arguments** – Each side submits arguments (max 5)
9. **Generate Verdict** – Click to generate AI-powered verdict
10. **View Results** – See verdict, reasoning, and winner

---

##  Design Features

- **Responsive Layout** – Works on desktop, tablet, and mobile
- **Bootstrap Components** – Consistent UI with Bootstrap 5
- **Color Coding** – Side A (Blue), Side B (Red) for clarity
- **Loading States** – Spinners for better UX
- **Gradients** – Modern gradient backgrounds on landing page
- **Icons** – Emoji icons for visual appeal

---

## Security Features

- JWT token-based authentication
- Protected routes using `ProtectedRoute` component
- Secure token storage in localStorage
- User validation before route access
- Role-based access control (Lawyer A/B)

---

##  Deployment

### Deploy to Vercel
```bash
npm install -g vercel
vercel
```

### Deploy
```bash
npm run build
# Deploy the 'dist' folder to Netlify
```

Update `VITE_API_URL` in `.env` to your production backend URL before deployment.

---

##  Troubleshooting

### Issue: "Failed to fetch" API errors
- Check if backend is running on `http://localhost:5000`
- Verify `VITE_API_URL` in `.env` matches your backend URL
- Check browser console for CORS errors

### Issue: User not logged in after refresh
- Verify JWT token is saved in localStorage
- Check if `localStorage.getItem('token')` returns a valid token
- Try logging in again

### Issue: Case arguments not showing
- Verify case has arguments submitted
- Check if verdict is generated (required to view arguments)
- Check backend logs for errors

---

##  Notes

- All API calls use JWT token in Authorization header
- Token expires in 30 days
- Case arguments limited to 5 per side
- AI verdict requires both sides to submit at least one argument

---

##  License

MIT License - Feel free to use this project for learning and development.

---

##  Author

**Chandu** - Full Stack Developer

---

##  Contributing

Contributions are welcome! Please feel free to submit issues or pull requests.

---
