💬 SocialSphere – A Modern Community Forum & Q&A Platform
<div align="center"> <br /> <img src="public/thumb.png" alt="Project Banner" /> <br /> <div> <img src="https://img.shields.io/badge/-React-61DAFB?style=for-the-badge&logo=react&logoColor=black" alt="React" /> <img src="https://img.shields.io/badge/-Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white" alt="Vite" /> <img src="https://img.shields.io/badge/-TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript" /> <img src="https://img.shields.io/badge/-Supabase-3ECF8E?style=for-the-badge&logo=supabase&logoColor=white" alt="Supabase" /> <img src="https://img.shields.io/badge/-TailwindCSS-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white" alt="Tailwind CSS" /> </div> <h3 align="center">Build Your Own Real-Time Social Community Platform</h3> <br /> </div>
📚 Table of Contents
Overview

Tech Stack

Features

Getting Started

Key Code Examples

Design & Assets

🚀 Overview
SocialSphere is a full-featured community forum and question-answer site built with modern web technologies. It supports GitHub login, real-time discussions, image uploads, community-based sorting, and beautiful glassmorphism UI. I created this to explore advanced frontend and backend integrations using Supabase and Vite.

⚙️ Tech Stack
🔹 React – Frontend UI

⚡ Vite – Lightning-fast dev server & build tool

🧠 TypeScript – Type-safe modern JS

🛠 Supabase – Auth, DB, real-time backend

🎨 Tailwind CSS – Responsive and fast styling framework

✨ Features
🔐 GitHub Authentication
Secure sign-in with GitHub OAuth, complete with profile display.

📝 Create & Share Posts
Users can share content and images in rich post cards.

👍👎 Voting System
Vote up or down with glowing visual effects and real-time updates.

💬 Threaded Commenting
Engage in meaningful discussions with nested replies.

🏷️ Community Organization
Posts are categorized by communities, giving it a Reddit-style feel.

🌈 Modern UI Design
Glassy layouts, gradient borders, glowing hover states — all mobile-responsive.

🔄 Real-Time Interactions
All user actions reflect instantly using Supabase subscriptions and React Query.

⚡ Getting Started
Prerequisites
Git

Node.js

npm

Setup Instructions
bash
Copy
Edit
git clone https://github.com/<your-username>/<your-repo>.git
cd your-project-folder
npm install
Environment Variables
Create a .env file in the root with your Supabase config:

env
Copy
Edit
VITE_SUPABASE_URL=https://your-project.supabase.co
VITE_SUPABASE_ANON_KEY=your-anon-key
Start the Dev Server
bash
Copy
Edit
npm run dev
Then open http://localhost:3000 in your browser 🚀

🧩 Key Code Examples
🔄 Supabase RPC with Vote & Comment Counts
sql
Copy
Edit
CREATE OR REPLACE FUNCTION get_posts_with_counts()
RETURNS TABLE (
  id integer,
  title text,
  content text,
  created_at timestamptz,
  image_url text,
  like_count integer,
  comment_count integer,
  user_avatar_url text
)
LANGUAGE sql
AS $$
  SELECT 
    p.id,
    p.title,
    p.content,
    p.created_at,
    p.image_url,
    (SELECT COUNT(*) FROM votes v WHERE v.post_id = p.id) AS like_count,
    (SELECT COUNT(*) FROM comments c WHERE c.post_id = p.id) AS comment_count,
    p.user_avatar_url
  FROM posts p
  ORDER BY p.created_at DESC;
$$;
🛡 Row Level Security for Vote Deletion
sql
Copy
Edit
ALTER TABLE votes ENABLE ROW LEVEL SECURITY;

CREATE POLICY "Delete own vote" ON votes
FOR DELETE
USING (auth.uid()::text = user_id);
🎨 Design & Assets
💡 Design Principles: Clean, glassmorphism-based UI with subtle gradients

🎨 Icons & Images: Optimized for modern web platforms

🧪 Inspiration Sources: Reddit, Dev.to, StackOverflow

🧠 Future Enhancements
🗂 User profiles with activity history

🧵 Custom threads & saved posts

📊 Analytics dashboard for community insights

🔔 Notification system (in progress)

🙌 Let's Connect
If you find this useful, feel free to ⭐ the repo and reach out with ideas, feedback, or collab interests!

Made with ❤️ by Simran