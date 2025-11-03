# React + JavaScript + Material Tailwind + shadcn/ui Project Setup Guide

This guide will walk you through setting up a React project with JavaScript (not TypeScript), Material Tailwind, and shadcn/ui from scratch.

## 📋 Project Stack

| Library           | Version                |
| ----------------- | ---------------------- |
| React             | **18.2.0**             |
| React DOM         | **18.2.0**             |
| Material Tailwind | **2.1.10**             |
| Tailwind CSS      | **3.4.14**             |
| TypeScript        | **5.3+**               |
| Vite              | **5+ or 7+ (both OK)** |
| shadcn/ui         | **latest**             |

---

## 🚀 Step-by-Step Installation

### Step 1: Create Vite Project

Run the following command to create a new React + JavaScript project:

```bash
npm create vite@latest project_name -- --template react
```

**Important:** When prompted, select the following options:
- **Use rolldown-vite (Experimental)?** → Select **No**
- **Install with npm and start now?** → Select **No**

You should see output like this:

```
> create-vite project_name --template react
|
o  Use rolldown-vite (Experimental)?:
|  No
|
o  Install with npm and start now?
|  No
|
o  Scaffolding project in E:\React\project_name...
|
—  Done. Now run:
  cd project_name
  npm install
  npm run dev
```

---

### Step 2: Navigate to Project Directory

```bash
cd project_name
```

---

### Step 3: Install React Dependencies

Install React and React DOM:

```bash
npm install react@18.2.0 react-dom@18.2.0
```

---

### Step 4: Install Material Tailwind

```bash
npm install @material-tailwind/react@2.1.10
```

---

### Step 5: Install Tailwind CSS

Install Tailwind CSS and its dependencies as dev dependencies:

```bash
npm install -D tailwindcss@3.4.14 postcss autoprefixer
```

---

### Step 6: Initialize Tailwind CSS

Generate Tailwind configuration files:

```bash
npx tailwindcss init -p
```

---

### Step 7: Configure Tailwind CSS

Open `tailwind.config.js` and replace everything with:

```javascript
const withMT = require("@material-tailwind/react/utils/withMT");

module.exports = withMT({
  content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
    "./node_modules/@material-tailwind/react/**/*.{js,ts,jsx,tsx}"
  ],
  theme: {
    extend: {},
  },
  plugins: [],
});
```

---

### Step 8: Add Tailwind Directives

Open `src/index.css` and make sure it contains:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

---

### Step 9: Update Vite Configuration

Open `vite.config.js` and replace its content with:

```javascript
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";
import path from "path";

export default defineConfig({
  plugins: [react()],
  resolve: {
    alias: {
      "@": path.resolve(__dirname, "./src"),
    },
  },
});
```

---

### Step 10: Create JavaScript Configuration File

For JavaScript projects, create a `jsconfig.json` file in the root directory:

```json
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@/*": ["./src/*"]
    }
  }
}
```

---

### Step 11: Initialize shadcn/ui

```bash
npx shadcn@latest init
```

Follow the prompts to complete the shadcn/ui setup.

---

## ✅ Running the Project

After completing all the steps above, start your development server:

```bash
npm run dev
```

Your project should now be running! Open your browser and navigate to the URL shown in the terminal (typically `http://localhost:5173`).

---

## 📝 Notes

- Make sure you have Node.js installed (version 16 or higher recommended)
- All configuration files should be in the root directory of your project
- The `@/` path alias allows you to import files from the `src` directory easily (e.g., `import Button from "@/components/Button"`)
- This setup uses **JavaScript** instead of TypeScript for a simpler configuration

---

## 🐛 Troubleshooting

If you encounter any issues:
1. Delete `node_modules` folder and `package-lock.json`
2. Run `npm install` again
3. Make sure all configuration files are correctly updated
4. Check that you're using compatible Node.js version
5. Verify that `jsconfig.json` exists in your root directory

---

## 🎉 You're All Set!

Your React JavaScript project with Material Tailwind and shadcn/ui is now ready for development. Happy coding!