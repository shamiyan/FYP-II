# TexPro ERP — Foundation

ASP.NET Core MVC + Web API + SQL Server solution for **TexPro Garments Pvt. Ltd.** (FYP, KIET). This week covers database, authentication, role menus, company setup, and document numbering.

## Open in Visual Studio

1. Open `TexProERP.sln` in Visual Studio (or `TexProERP.slnx`).
2. Set **TexProERP.Web** as the startup project for the browser UI.
3. SQL Server LocalDB is used by default: `(localdb)\mssqllocaldb` / database `TexProERP`.
4. First run applies EF Core migrations and seeds master data.

## Demo users

Password for every seeded user: **`TexPro@123`**

| Code | Role | Email |
|------|------|--------|
| AD1 | Admin | admin@tex-pro.com |
| INV1 | Inventory Officer | inventory@tex-pro.com |
| SO1 | Sales Officer | sales@tex-pro.com |
| PL1 | Production Planner | production.planner@tex-pro.com |
| QC1 | QC Officer | quality.check@tex-pro.com |
| FIN1 | Finance Officer | finance@tex-pro.com |

## Projects

- `TexProERP.Web` — MVC master layout, cookie login, role-based menu, company and numbering screens.
- `TexProERP.Api` — JWT login at `POST /api/auth/login` for a future mobile client.
- `TexProERP.Infrastructure` — EF Core `TexProDbContext` and seed data.
- `TexProERP.Core` — entities and permission codes.

## API login example

```http
POST http://localhost:5184/api/auth/login
Content-Type: application/json

{ "email": "admin@tex-pro.com", "password": "TexPro@123" }
```

## What is built now (FYP-2 roadmap start)

Foundation is kept. Admin can **edit the role matrix** (checkboxes per role; applies to every user of that role) and **extra permissions per user**. Master data, inventory, sales (quotation → SO → ATP → approval → delivery/PGI → invoice → payment), returns, production/QC, alerts and audit are on the web app. Forms use required fields, ranges, unique codes, stock checks and anti-forgery tokens.

Log in as `admin@tex-pro.com` / `TexPro@123`, open **Role matrix**, tick rights, save. Then open a user and tick extra rights for that person only.

## Deliverables

- ERD: `docs/erd.md`
- Architecture: `docs/architecture.md`
- Schema script: `docs/schema.sql`
