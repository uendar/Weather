#  Weather Forecasting App

This is a **full-stack weather forecasting application** built using **FastAPI (backend) and React (frontend)**. The system collects and visualizes **real-time weather data** from IoT sensors and **user-submitted forecasts**. It also allows users to **view historical temperature data** with interactive graphs and downloadable CSV reports.

## Features

✅ **Weather Widget**: Displays real-time weather & forecasts  
✅ **User Forecasts**: Users can create, update, and delete forecasts  
✅ **Temperature Visualization**: View actual vs. predicted weather in charts  
✅ **Historical Data Download**: Export past weather data in CSV format  
✅ **API Integration**: Backend is built with **FastAPI**, using **PostgreSQL & Redis**  
✅ **Fully Dockerized**: Supports **Docker Compose** for easy deployment  

---

##  **Tech Stack**
###  Backend (FastAPI)
- **FastAPI** - Python web framework
- **PostgreSQL** - Relational database
- **Redis** - Caching system
- **SQLAlchemy & Alembic** - ORM & database migrations
- **Uvicorn** - ASGI server

###  Frontend (React)
- **React (TypeScript)** - UI framework
- **Mantine UI** - Component library
- **TanStack Query** - API data fetching
- **Axios** - HTTP client
- **Recharts** - Charts and graphs
- **Docker** - Containerized deployment

---

##  **Project Structure**
```
weather/
│── backend/                 # FastAPI backend
│   ├── models/              # Database models
│   ├── routes/              # API endpoints
│   ├── schemas/             # Pydantic validation
│   ├── services/            # Business logic
│   ├── database.py          # Database config
│   ├── main.py              # FastAPI entry point
│   ├── Dockerfile           # Backend Dockerfile
│   ├── requirements.txt     # Backend dependencies
│   ├── docker-compose.yml   # Docker setup (for full-stack)
│
│── frontend/                # React frontend
│   ├── src/                 # Frontend source code
│   ├── components/          # UI components
│   ├── context/             # React Context API
│   ├── hooks/               # Custom hooks
│   ├── api/                 # API integrations
│   ├── Dockerfile           # Frontend Dockerfile
│   ├── package.json         # Frontend dependencies
│   ├── public/              # Static assets
│   ├── .env                 # Frontend environment variables
│
│── docker-compose.yml       # Unified Docker Compose
│── README.md                # Project documentation
```

---

##  **Setup & Installation**

### 1️ **Clone the Repository**
```sh
git clone https://github.com/uendar/weather-app.git
cd weather
```

---

## 🏢 **Backend Setup (FastAPI)**
### 2️ **Configure Environment Variables**
Create a **`.env`** file inside `backend/` and add:
```sh
DATABASE_URL=postgresql+asyncpg://postgres:your_password@db:5432/weather_db
REDIS_URL=redis://redis:6379
```

### 3️ **Run Backend (Without Docker)**
```sh
cd backend
pip install -r requirements.txt
uvicorn main:app --reload
```

---

##  **Frontend Setup (React)**
### 4️ **Install Frontend Dependencies**
```sh
cd frontend
npm install
```

### 5️ **Start the Frontend**
```sh
npm start
```
The frontend will be available at `http://localhost:3000`.

### 6️ **Set API Base URL**
Create a `.env` file in **frontend/** and add:
```sh
REACT_APP_API_BASE_URL=http://localhost:8000
```

---

## 🐛 **Docker Setup (Full Stack)**
To run the **entire project (backend + frontend + DB + Redis)** in Docker:

### 7️ **Build and Start the Containers**
```sh
docker-compose up --build
```
- Backend: `http://localhost:8000/docs`
- Frontend: `http://localhost:3000`
- PostgreSQL: `localhost:5433`
- Redis: `localhost:6379`

### 8️ **Stop the Containers**
```sh
docker-compose down
```

---

## **API Endpoints**
| Method  | Endpoint                 | Description                                      |
|---------|--------------------------|--------------------------------------------------|
| `GET`   | `/weather/{city}`        | Fetch current & predicted weather for a city    |
| `POST`  | `/forecasts`             | Submit a user weather forecast                  |
| `PUT`   | `/forecasts/{id}`        | Update an existing forecast                     |
| `DELETE`| `/forecasts/{id}`        | Delete a forecast                               |
| `GET`   | `/temperature/{city}`    | Get past weather temperature (actual & forecast)|
| `GET`   | `/temperature/{city}/download` | Download CSV with temperature data     |

---

##  **Useful Docker & Debugging Commands**
### View Running Containers:
```sh
docker ps
```
### View Logs:
```sh
docker logs fastapi-weather-backend
```
### Connect to PostgreSQL:
```sh
docker exec -it weather-db psql -U postgres -d weather_db
```
### Run Alembic Migrations:
```sh
docker exec -it fastapi-weather-backend alembic upgrade head
```
### Clear Redis Cache:
```sh
docker exec -it weather-redis redis-cli FLUSHALL
```

---

## **Frontend UI Components**
- **Weather Widget**: Displays weather data
- **Forecast Table**: Manage forecasts (CRUD)
- **Temperature Chart**: View historical weather data
- **CSV Download**: Export temperature history

---

## **Contributing**
1️ Fork the repo  
2️ Create a new branch: `git checkout -b feature-branch`  
3️ Make changes & commit: `git commit -m "Added new feature"`  
4️ Push changes: `git push origin feature-branch`  
5️ Open a Pull Request  

---
