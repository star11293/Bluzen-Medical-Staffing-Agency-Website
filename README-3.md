# Bluzen Medical Healthcare Staffing Agency

A full-stack healthcare staffing platform that connects medical professionals with employers. The project pairs a multi-page marketing website with a Flask-powered job board featuring role-based authentication, job posting and application workflows, and automated job alert notifications.

**Live site (frontend):** Hosted on Netlify  
**Job board (backend):** Hosted on Heroku

---

## Features

### Marketing Website (Static HTML/CSS)

- **Home** — Hero section, services overview, and calls to action for employers and job seekers
- **About** — Company mission, values, and team information
- **Services** — Detailed breakdown of staffing solutions offered
- **Job Listings** — Browse available healthcare positions
- **Employment Forms** — Online application forms for prospective employees
- **CPR Training** — Information and resources for CPR certification
- **Calendar** — Scheduling and availability calendar
- **Contact** — Inquiry form and contact details
- **Privacy Policy** — Data handling and privacy disclosures

### Job Board Application (Flask)

- **Role-Based Authentication** — Separate registration and login flows for employers and job seekers using Flask-Login
- **Job Posting** — Employers can create listings with title, description, location, type, qualifications, pay rate, company name, and contact info
- **Job Applications** — Seekers can browse listings and submit applications with resume text and cover letters
- **Job Alerts** — Subscribers save search criteria (keywords, location, job type) and get notified when new postings match
- **SQLite Database** — Lightweight relational storage via Flask-SQLAlchemy

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | HTML5, CSS3 (inline + external stylesheets) |
| Backend | Python, Flask 3.1 |
| ORM | Flask-SQLAlchemy (SQLite) |
| Auth | Flask-Login, Werkzeug password hashing |
| Templating | Jinja2 |
| Deployment | Netlify (static pages), Heroku (Flask app via Gunicorn) |

---

## Project Structure

```
Bluzen-Medical-Staffing-Agency-Website/
├── index.html                 # Landing page
├── about_page.html            # About the agency
├── services_page.html         # Services offered
├── contact_page.html          # Contact form
├── job_listings.html          # Static job listings page
├── job_posting.html           # Job posting info page
├── employment_form.html       # Employment application (v1)
├── employment_form2.html      # Employment application (v2)
├── cpr_page.html              # CPR training resources
├── calendar_light_blue.html   # Calendar / scheduling
├── privacy_policy.html        # Privacy policy
├── _redirects                 # Netlify → Heroku proxy rules
├── Procfile                   # Heroku process definition
├── requirements.txt           # Python dependencies
└── job_board_project/
    ├── app.py                 # Flask application (models, routes, logic)
    ├── static/
    │   └── style.css          # Job board styles
    └── templates/
        ├── base.html          # Jinja2 base layout
        ├── index.html         # Job board home
        ├── register.html      # User registration
        ├── login.html         # User login
        ├── jobs.html          # Job listings
        ├── job_detail.html    # Single job view
        ├── post_job.html      # Create a job (employers)
        └── alerts.html        # Manage job alerts
```

---

## Getting Started

### Prerequisites

- Python 3.10+
- pip

### Installation

```bash
# Clone the repository
git clone https://github.com/star11293/Bluzen-Medical-Staffing-Agency-Website.git
cd Bluzen-Medical-Staffing-Agency-Website

# Install dependencies
pip install -r requirements.txt
```

### Running the Job Board Locally

```bash
python job_board_project/app.py
```

The Flask development server will start at `http://127.0.0.1:5000`. The SQLite database is created automatically on first run.

### Viewing the Static Site

Open any of the HTML files directly in a browser, or serve them with a simple HTTP server:

```bash
python -m http.server 8000
```

Then visit `http://localhost:8000` in your browser.

---

## Deployment

### Static Frontend (Netlify)

The HTML pages are deployed directly to Netlify. The `_redirects` file proxies `/jobs` routes to the Heroku-hosted Flask backend so the job board is accessible from the same domain.

### Job Board Backend (Heroku)

The `Procfile` tells Heroku to run the Flask app with Gunicorn:

```
web: gunicorn job_board_project.app:app
```

---

## Database Models

- **User** — Stores username, email, hashed password, and role (`employer` or `seeker`)
- **Job** — Represents a posting with title, description, location, type, qualifications, pay rate, company/contact info, and timestamps
- **Application** — Links a seeker to a job with resume text and optional cover letter
- **JobAlert** — Saved search subscription with keyword, location, and job type filters

---

## Roadmap

- [ ] Integrate a production email service (SendGrid / Amazon SES) for job alerts
- [ ] Add resume file upload support
- [ ] Migrate from SQLite to PostgreSQL for production
- [ ] Build an admin dashboard for managing users and postings
- [ ] Add search and filtering on the job listings page

---

## License

This project does not currently specify a license. Contact the repository owner for usage permissions.

---

## Author

Built by [star11293](https://github.com/star11293)
