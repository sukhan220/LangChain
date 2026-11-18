# LangChain Learning Journey | ল্যাংচেন শেখার প্রজেক্ট

🌐 **Select Language / ভাষা নির্বাচন করুন:** [**বাংলা**](#-বাংলা-সংস্করণ) | [**English**](#-english-version)

---

<a name="-বাংলা-সংস্করণ"></a>
## 🇧🇩 বাংলা সংস্করণ

এটি LangChain এবং Python ব্যবহার করে এআই (AI) এবং লার্জ ল্যাঙ্গুয়েজ মডেল (LLM) নিয়ে কাজ শেখার একটি প্রজেক্ট। এই প্রজেক্টে `uv` প্যাকেজ ম্যানেজার ব্যবহার করে খুব দ্রুত ডিপেন্ডেন্সি ম্যানেজ করা হয়েছে এবং জুপিটার নোটবুকের মাধ্যমে ধাপে ধাপে প্র্যাকটিস করা হচ্ছে।

### 🚀 প্রজেক্ট সেটআপ ও ইনস্টলেশন গাইড

আপনার কম্পিউটারে প্রজেক্টটি নামানোর পর রান করার জন্য নিচের ধাপগুলো অনুসরণ করুন:

#### ১. প্রজেক্ট ইনিশিয়ালাইজ ও ভার্চুয়াল এনভায়রনমেন্ট তৈরি করা
প্রজেক্টের রুট ফোল্ডারে টার্মিনাল ওপেন করে প্রজেক্ট ইনিশিয়ালাইজ এবং পাইথনের ভার্চুয়াল এনভায়রনমেন্ট তৈরি করুন:
```bash
uv init
uv venv
```

এরপর এনভায়রনমেন্টটি অ্যাক্টিভেট করুন:
* **Windows (PowerShell/CMD):**
  ```bash
  .venv\Scripts\activate
  ```
* **macOS / Linux:**
  ```bash
  source .venv/bin/activate
  ```

#### ২. রিকোয়েমেন্ট ফাইল থেকে প্যাকেজ ইনস্টল করা
প্রজেক্টের প্রয়োজনীয় সব লাইব্রেরি (LangChain, OpenAI, IPyKernel ইত্যাদি) একসঙ্গে ইনস্টল করতে নিচের কমান্ডটি দিন:
```bash
uv add -r requirements.txt
```

### 🔑 OpenAI API Key কনফিগারেশন

মডেলগুলো কাজ করার জন্য আপনার একটি ওপেনএআই (OpenAI) এপিআই কি (API Key) প্রয়োজন হবে। এটি সেটআপ করার নিয়ম:

1. প্রথমে [OpenAI Platform](https://platform.openai.com/)-এ গিয়ে লগইন করুন এবং ড্যাশবোর্ড থেকে **API keys** সেকশনে যান।
2. **"Create new secret key"** এ ক্লিক করে একটি নতুন কি তৈরি করুন এবং তা কপি করে নিরাপদ স্থানে রাখুন।
3. প্রজেক্টের মূল ফোল্ডারে একটি **`.env`** ফাইল তৈরি করুন এবং আপনার কি-টি নিচের মতো করে যুক্ত করুন:
   ```env
   OPENAI_API_KEY=your_actual_api_key_here
   ```

### 📂 প্রজেক্ট স্ট্রাকচার

* `notebooks/` – ল্যাংচেনের বিভিন্ন ধাপের প্র্যাকটিস করার জুপিটার নোটবুক ফাইলগুলো এখানে থাকবে।
* `src/` – মূল সোর্স কোড বা মডিউল ফাইল।
* `requirements.txt` – প্রজেক্টের সমস্ত পাইথন ডিপেন্ডেন্সির তালিকা।
* `.env` – সিক্রেট এপিআই কি সংরক্ষণের জন্য (গিটহাবে আপলোড করা যাবে না)।

### 💻 যেভাবে নোটবুক রান করবেন
1. ভিএস কোডে (VS Code) গিয়ে `notebooks/` ফোল্ডারের ভেতরের নোটবুক ফাইলটি ওপেন করুন।
2. নোটবুকের ওপরের ডান কোণায় কার্নেল হিসেবে **`Python (LangChain)`** বা ভার্চুয়াল এনভায়রনমেন্ট সিলেক্ট করুন।
3. কোড সেলগুলোতে `Shift + Enter` চেপে রান করুন।

### 📝 প্রথম পাঠ: বেসিক চ্যাট মডেল (`01_basic_chat.ipynb`)

আপনার `notebooks/01_basic_chat.ipynb` ফাইলের ভেতরে নিচের কোড ও নোটগুলো সাজিয়ে নিতে পারেন:

#### সেল ১ (Markdown):
```markdown
# ১. বেসিক চ্যাট মডেল (Basic Chat Model) - LangChain
এই নোটবুকে আমরা শিখব কীভাবে LangChain ব্যবহার করে OpenAI-এর চ্যাট মডেলের সাথে সংযোগ স্থাপন করতে হয় এবং `.invoke()` মেথডের মাধ্যমে মেসেজ পাঠাতে হয়।
```

#### সেল ২ (Code - লাইব্রেরি এবং এনভায়রনমেন্ট লোড করা):
```python
import os
from dotenv import load_dotenv
from langchain_openai import ChatOpenAI

# .env ফাইল থেকে API Key লোড করা
load_dotenv()
```

#### সেল ৩ (Markdown):
```markdown
এখন আমরা চ্যাট মডেলটি ইনিশিয়ালাইজ করব এবং মডেলকে একটি প্রশ্ন পাঠাব।
```

#### সেল ৪ (Code - মডেল কল করা এবং আউটপুট দেখা):
```python
# চ্যাট মডেল ইনিশিয়ালাইজ করা (gpt-3.5-turbo ব্যবহার করা হচ্ছে)
llm = ChatOpenAI(model="gpt-3.5-turbo")

# মডেলকে বাংলায় প্রম্পট পাঠানো
response = llm.invoke("Hi! LangChain এবং পাইথন নিয়ে আমার যাত্রা শুরু হলো। বাংলায় উৎসাহমূলক এক লাইন কিছু বলো।")

# আউটপুট প্রিন্ট করা
print("AI-এর উত্তর:")
print(response.content)
```

[⬆️ ওপরে ফিরে যান / Back to Top](#langchain-learning-journey--ল্যাংচেন-শেখার-প্রজেক্ট)

---

<a name="-english-version"></a>
## 🇺🇸 English Version

This is a hands-on learning project for building AI and Large Language Model (LLM) applications using LangChain and Python. The project leverages the `uv` package manager for blazing-fast dependency management and uses Jupyter Notebooks for step-by-step interactive practice.

### 🚀 Project Setup & Installation Guide

Follow these steps to set up and run the project on your local machine:

#### 1. Initialize Project & Create Virtual Environment
Open your terminal in the project root directory to initialize the project and create a virtual environment:
```bash
uv init
uv venv
```

Activate the virtual environment:
* **Windows (PowerShell/CMD):**
  ```bash
  .venv\Scripts\activate
  ```
* **macOS / Linux:**
  ```bash
  source venv/bin/activate
  ```

#### 2. Install Packages from Requirements
Install all necessary project libraries (LangChain, OpenAI, IPyKernel, etc.) at once using:
```bash
uv add -r requirements.txt
```

### 🔑 OpenAI API Key Configuration

To interact with the models, you will need an OpenAI API Key. Follow these steps to configure it:

1. Go to the [OpenAI Platform](https://platform.openai.com/), log in, and navigate to the **API keys** section from the dashboard.
2. Click **"Create new secret key"**, generate a new key, and copy it to a safe place.
3. Create a **`.env`** file in the root directory of your project and add your key as follows:
   ```env
   OPENAI_API_KEY=your_actual_api_key_here
   ```

### 📂 Project Structure

* `notebooks/` – Contains Jupyter Notebook files for practicing different LangChain modules step-by-step.
* `src/` – Core source code and module files.
* `requirements.txt` – List of all Python dependencies for the project.
* `.env` – Stores secret API keys (must be ignored by Git).

### 💻 How to Run the Notebooks
1. Open the notebook file inside the `notebooks/` folder using VS Code.
2. Select **`Python (LangChain)`** (or your `.venv` environment) as the kernel from the top-right corner of the notebook.
3. Press `Shift + Enter` to execute the code cells sequentially.

### 📝 Lesson 1: Basic Chat Model (`01_basic_chat.ipynb`)

Structure your `notebooks/01_basic_chat.ipynb` file with the following cells and notes:

#### Cell 1 (Markdown):
```markdown
# 1. Basic Chat Model - LangChain
In this notebook, we will learn how to connect to OpenAI's chat model using LangChain and send prompts via the `.invoke()` method.
```

#### Cell 2 (Code - Load Libraries & Environment):
```python
import os
from dotenv import load_dotenv
from langchain_openai import ChatOpenAI

# Load API Key from the .env file
load_dotenv()
```

#### Cell 3 (Markdown):
```markdown
Now let's initialize the chat model and send a prompt to get a response.
```

#### Cell 4 (Code - Invoke Model & Print Output):
```python
# Initialize the chat model (using gpt-3.5-turbo)
llm = ChatOpenAI(model="gpt-3.5-turbo")

# Send a prompt to the model
response = llm.invoke("Hi! I just started my journey with LangChain and Python. Give me a one-line motivational quote.")

# Print the output
print("AI Response:")
print(response.content)
```

[⬆️ Back to Top / ওপরে ফিরে যান](#langchain-learning-journey--ল্যাংচেন-শেখার-প্রজেক্ট)