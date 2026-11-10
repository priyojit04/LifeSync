# LifeSync Website Frontend
Responsive React + Vite frontend starter using the approved cream / forest-green LifeSync design.

## Included
Homepage, five modules, feature overview, dashboard preview, Premium (Weekly ₹15 / Monthly ₹59 / Yearly ₹499), Wallet and UPI/QR placeholder, referral rewards (₹10 referrer / ₹5 new user), AI preview, APK version center, login/register UI, multilingual selector and support.

## Run
Install Node.js LTS, extract ZIP, open terminal in this folder:
`npm install`
`npm run dev`

## Important: backend integration still required
This is a frontend starter/prototype, not a production-connected website. Forms and actions show informational messages. No payment is processed and no fake QR/UPI credentials are included.

Connect the existing Supabase project using `@supabase/supabase-js` and `.env` values. Implement Auth, session handling, user dashboard reads, payment settings from `payment_settings`, QR image from the configured storage bucket, and the existing secured RPCs/RLS for wallet recharge, activation, Premium purchase, referrals and admin actions. Add real admin-only routes and verify all access controls. Never expose a service-role key in frontend code.

APK center is prepared for actual tested releases. Android compatibility must be verified per release/device; do not claim universal compatibility without testing. Dashboard metrics are illustrative.

## Supabase Authentication setup

This build includes Supabase email/password registration, login, logout, and password-reset email support.

1. The supplied `.env` file is prefilled with this project's Supabase URL and browser-safe publishable key. Do not add a `service_role` or secret key to a frontend project.
2. Run `npm install`, then `npm run dev`.
3. In Supabase Dashboard, open **Authentication → URL Configuration**. Add your local URL (for example `http://localhost:5173`) to **Redirect URLs**. For a deployed site, add its HTTPS URL too and set the production Site URL.
4. In **Authentication → Providers → Email**, choose whether email confirmation is required. If enabled, new users must confirm their email before a session is established.

Registration sends full name, phone number, and optional referral code as Supabase Auth user metadata. This frontend does not directly insert rows into application profile, wallet, or referral tables; those must be handled by your existing secure database trigger/RPC and RLS policies. Premium and wallet payments are not activated by this authentication integration.
