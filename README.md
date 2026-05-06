# Extension-chrome-
Rananisar SB5121 Chrome Extension is a lightweight browser tool designed to enhance Chrome functionality with custom automation, UI utilities, or web interaction features. It integrates directly with background-based operations and user-triggered actions without affecting performance. browsers to provide
/extension
  manifest.json
  content.js
  popup.html
  popup.js
  styles.css{
  "manifest_version": 3,
  "name": "Auto Template Replacer",
  "version": "1.0",
  "description": "Reusable template auto replacement for social posts",
  "permissions": ["storage", "activeTab", "scripting"],
  "action": {
    "default_popup": "popup.html"
  },
  "content_scripts": [
    {
      "matches": ["https://*.facebook.com/*", "https://*.twitter.com/*", "https://*.linkedin.com/*"],
      "js": ["content.js"]
    }
  ]
}function applyTemplate(template, data) {
  let output = template

  Object.keys(data).forEach(key => {
    const regex = new RegExp(`{{${key}}}`, 'g')
    output = output.replace(regex, data[key])
  })

  return output
}

function injectText(text) {
  const el = document.activeElement
  if (!el) return

  if (el.tagName === 'TEXTAREA' || el.isContentEditable) {
    el.value = text
    el.innerText = text
  }
}

chrome.runtime.onMessage.addListener((msg) => {
  if (msg.type === 'INSERT_TEMPLATE') {
    const result = applyTemplate(msg.template, msg.data)
    injectText(result)
  }
})<!DOCTYPE html>
<html>
<head>
  <link rel="stylesheet" href="styles.css">
</head>
<body>

<h3>Template Generator</h3>

<textarea id="template" placeholder="Write template..."></textarea>

<input id="name" placeholder="Name">
<input id="message" placeholder="Message">

<button id="apply">Apply</button>

<script src="popup.js"></script>
</body>
</html>document.getElementById('apply').onclick = async () => {
  const template = document.getElementById('template').value

  const data = {
    name: document.getElementById('name').value,
    message: document.getElementById('message').value
  }

  const [tab] = await chrome.tabs.query({ active: true, currentWindow: true })
{{name}} — Digital Creator 🎯

{{message}}{
  "manifest_version": 3,
  "name": "AI Auto Content Engine",
  "version": "2.0",
  "description": "AI-powered social post generator",
  "permissions": ["storage", "activeTab", "scripting"],
  "host_permissions": ["https://api.openai.com/*"],
  "action": {
    "default_popup": "popup.html"
  },
  "content_scripts": [
    {
      "matches": [
        "https://*.facebook.com/*",
        "https://*.twitter.com/*",
        "https://*.linkedin.com/*"
      ],
      "js": ["content.js"]
    }
  ]
}

💡 Real system  
💸 Real earning  
📈 Step-by-step method  

🚀 Start today
  chrome.tabs.sendMessage(tab.id, {
    type: 'INSERT_TEMPLATE',1. Open Chrome
2. Go to chrome://extensions/
3. Enable Developer Mode1. Open Facebook / Twitter / LinkedIn
2. Click extension
3. Paste template
4. Fill inputs
5. Click APPLY
6. Text auto-inserts into post box
4. Click "Load unpacked"
5. Select /extension folder
    template,
    data
  })/extension
  manifest.json
  content.js
  popup.html
  popup.js
  ai.js
  storage.js
  styles.css
}function injectText(text) {
  const el = document.activeElement
  if (!el) return

  if (el.tagName === 'TEXTAREA' || el.isContentEditable) {
    el.value = text
    el.innerText = text
  }
}
function save(key, value) {
  chrome.storage.local.set({ [key]: value })
}

function load(key) {
  return new Promise(resolve => {
    chrome.storage.local.get([key], result => {
      resolve(result[key])
    })
  })
}

export { save, load }
chrome.runtime.onMessage.addListener((msg) => {
  if (msg.type === 'INSERT_AI_CONTENT') {
    injectText(msg.text)
  }
})async function generateAIContent(prompt, apiKey) {
  const res = await fetch("https://api.openai.com/v1/chat/completions", {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
      "Authorization": "Bearer " + apiKey
    },
    body: JSON.stringify({
      model: "gpt-4o-mini",
      messages: [
        {
          role: "user",
          content: prompt
        }
      ]
    })
  })

  const data = await res.json()
  return data.choices[0].message.content
}

export { generateAIContent }<!DOCTYPE html>
<html>
<head>
  <link rel="stylesheet" href="styles.css">
</head>
<body>

<h3>AI Content Generator</h3>

<textarea id="prompt" placeholder="Enter idea..."></textarea>

<input id="apiKey" placeholder="OpenAI API Key">

<button id="generate">Generate</button>
<button id="insert">Insert</button>

<textarea id="output" placeholder="AI Output"></textarea>

<script type="module" src="popup.js"></script>
</body>
</html>import { generateAIContent } from './ai.js'
import { save, load } from './storage.js'

let generatedText = ""

document.getElementById('generate').onclick = async () => {
  const prompt = document.getElementById('prompt').value
  const apiKey = document.getElementById('apiKey').value

  await save("apiKey", apiKey)

  const result = await generateAIContent(prompt, apiKey)

  generatedText = result
  document.getElementById('output').value = result
}

document.getElementById('insert').onclick = async () => {
  const [tab] = await chrome.tabs.query({ active: true, currentWindow: true })

  chrome.tabs.sendMessage(tab.id, {
    type: "INSERT_AI_CONTENT",
    text: generatedText
  })
}

window.onload = async () => {
  const key = await load("apiKey")
  if (key) document.getElementById('apiKey').value = key
}body {
  font-family: Arial;
  padding: 10px;
  width: 320px;- Never expose API key in frontend (move to backend proxy for production)
- Rate limit AI calls
- Validate prompt input
- Encrypt stored API key (optional upgrade)Input:
"Best AI tools for earning online"

Output:
"Best AI tools for earning online 👉 https://yourdomain.com/ref/abc123"
Support dynamic link generation via backend API
}

textarea {
  width: 100%;
  height: 80px;
  margin-bottom: 10px;
}

input {
  width: 100%;
  margin-bottom: 10px;
}

button {
  width: 100%;
  margin-bottom: 5px;
  padding: 10px;
  background: black;
  color: white;
  border: none;
}1. Open social site
2. Click extension
3. Enter prompt (e.g. "affiliate marketing post")
4. Add API key
5. Click GENERATE
6. Click INSERT
7. Auto post content insertedchrome://extensions/
Enable Developer Mode
Load unpacked → /extension# Clone repo
git clone https://github.com/rananisarsb51214-web/Extension-chrome-.wiki.git
# Step 1: create new repo
gh repo create extension-chrome-ai --public# clone wiki
git clone https://github.com/rananisarsb51214-web/Extension-chrome-.wiki.git

# copy files manually into new repo folder
cp -r Extension-chrome-.wiki/* extension-chrome-ai/

# Step 2: clone it
git clone https://github.com/rananisarsb51214-web/extension-chrome-ai.git

cd extension-chrome-ai
cd Extension-chrome-.wiki

# Copy your extension files into this folder
# (manifest.json, content.js, popup.js, etc.)

# Initialize if needed
git init

# Add all files
git add .

# Commit
git commit -m "Add AI multi-platform affiliate Chrome extension"

# Set main branch
git branch -M main

# Connect remote (if not already)
git remote add origin https://github.com/rananisarsb51214-web/Extension-chrome-.wiki.git

# Push
git push -u origin mainchrome://extensions/
Enable Developer Mode
Load unpacked → select your project folder# Install gh CLI
npm install -g gh

# Create repo from CLI
gh repo create extension-chrome-ai --public --source=. --pushchrome://extensions/
Enable Developer Mode
Load unpacked → select extension-chrome-ai/extension
  manifest.json
  content.js
  popup.js
  ...
/scripts
  build.js
.github/workflows
  release.yml
update.xml
package.json{
  "name": "ai-extension",
  "version": "1.0.0",
  "scripts": {
    "build": "node scripts/build.js",
    "release": "npm version patch && git push --follow-tags"
  }
}const fs = require('fs')
const archiver = require('archiver')

const output = fs.createWriteStream('extension.zip')
const archive = archiver('zip')

archive.pipe(output)

archive.directory('extension/', false)

archive.finalize()npm install archiver<?xml version='1.0' encoding='UTF-8'?>
<gupdate xmlns="http://www.google.com/update2/response" protocol="2.0">
  <app appid="YOUR_EXTENSION_ID">
    <updatecheck codebase="https://yourdomain.com/extension.zip" version="1.0.1"/>
  </app>
</gupdate>name: Build & Release Extension

on:
  push:
    tags:
      - 'v*'

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout
        uses: actions/checkout@v3

      - name: Install Node
        uses: actions/setup-node@v3
        with:
          node-version: 18

      - name: Install deps
        run: npm install

      - name: Build ZIP
        run: npm run build

      - name: Upload Artifact
        uses: actions/upload-artifact@v3
        with:
          name: extension
          path: extension.zip

      - name: Release
        uses: softprops/action-gh-release@v1
        with:
          files: extension.zip
