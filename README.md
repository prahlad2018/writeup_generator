🧠 Overview
This Python script automates the generation of Operations and Maintenance RCA write-up documents. It reads a user-provided issue prompt (issue_prompt.txt), uses the OpenAI ChatGPT API to generate detailed RCA field content, and fills a structured Word template (Writeup_template.docx) by replacing placeholders like <<root_cause>>, <<workaround>>, etc.

✅ Key Features
Uses OpenAI GPT-4 API via raw HTTPS (no SDK required)

Only generates content for fields mentioned in the prompt

Replaces structured <<placeholder>> tags in a .docx template

Saves the final output as a new Word document using the PIM number

📁 Project Structure

writeup_generator/
├── generate_writeup_from_prompt_api.py     # Main script
├── issue_prompt.txt                        # Input: raw issue details
├── Writeup_template.docx                   # Input: Word template with placeholders
├── Writeup_PIM-<number>.docx               # Output: Generated write-up file
└── README.md                               # Project documentation
🛠️ Setup Instructions
Install dependencies

bash
Copy
Edit
pip install requests python-docx
Get your OpenAI API Key

Go to: https://platform.openai.com/account/api-keys

Copy your key and replace "your_openai_api_key" in the script

📝 How to Use
Edit issue_prompt.txt

Include real issue details like:

text
Copy
Edit
PIM-153273

Root Cause:
A null check was missing in the income flag update logic.

Workaround:
Temporary exclusion added in code.

...
Prepare your Writeup_template.docx

Use <<field_name>> style tags like:

text
Copy
Edit
<<pim_number>>
<<root_cause>>
<<workaround>>
<<rca_validation>>
...
Run the script

python generate_writeup_from_prompt_api.py

Find your output

Look for a file named like:

Writeup_PIM-153273.docx
It will contain the AI-generated, cleanly formatted write-up.

🔒 Security Note
Keep your API_KEY secure. Avoid hardcoding it in shared files or committing it to version control.

You can also load it from an environment variable:

import os
API_KEY = os.getenv("OPENAI_API_KEY")

📌 Customization Ideas
Add “Not Provided” fallback for missing fields

Export to PDF

Add GUI to upload prompt and download file

Add retry/backoff logic on API error (429)

