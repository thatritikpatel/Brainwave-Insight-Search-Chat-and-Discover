# Brainwave Insight Search: Chat and Discover ✨

## Overview 📃

**Brainwave Insight Search: Chat and Discover** is an innovative AI-powered tool designed to streamline research and discovery processes. Leveraging state-of-the-art language models and integrations with knowledge repositories like ArXiv, Wikipedia, and DuckDuckGo, this application provides users with instant access to relevant and concise information, empowering them to explore, learn, and achieve insights effortlessly.

---

## Video Demo

Here's a video demo of the project:

https://github.com/user-attachments/assets/0108c206-6928-46a7-85f7-66519021b998

---

## Why Brainwave Insight Search? 🚀

In the age of information overload, finding accurate and relevant information can be daunting. Traditional search engines often inundate users with irrelevant results, while the manual process of sifting through articles is time-consuming and inefficient. 

**Brainwave Insight Search** addresses these challenges by:

- ⏳ Simplifying the search process with conversational queries.
- 🔎 Providing curated and precise results from reliable sources.
- ♻️ Saving valuable time for researchers, students, and professionals.

---

## What Does It Do? 🎨

- **🖊️ Natural Language Interaction:** Users can input queries in plain English.
- **📈 Multi-Source Integration:** It fetches information from multiple sources, including:
  - **ArXiv:** Access to academic papers and preprints.
  - **Wikipedia:** General knowledge repository.
  - **DuckDuckGo:** Web-wide search for diverse perspectives.
- **🤖 Dynamic Query Processing:** The app uses advanced tools and APIs to retrieve the most relevant content tailored to the user’s query.

---

## How Does It Work? ⚙️

### Key Components:

1. **Streamlit for UI 🎡**
   - Provides a sleek, interactive user interface for real-time interaction.

2. **LangChain Framework ⚡**
   - Aids in orchestrating complex tasks and connecting multiple tools seamlessly.

3. **ChatGroq Model 🧠**
   - An advanced language model (e.g., `Gemma2-9b-It` or `Llama3-8b-8192`) processes user queries and generates coherent, contextual responses.

4. **APIs and Wrappers 🔄**
   - **ArXivAPIWrapper**: Retrieves academic papers with abstract-level details.
   - **WikipediaAPIWrapper**: Fetches summarized articles from Wikipedia.
   - **DuckDuckGoSearchRun**: Conducts broad web searches for additional information.

5. **Agent Initialization 🤖**
   - Combines these tools into a unified agent using LangChain’s `initialize_agent` function, enabling coordinated, multi-source querying.

### Code Workflow 🔠:

```python
import streamlit as st
from langchain_groq import ChatGroq
from langchain_community.utilities import ArxivAPIWrapper, WikipediaAPIWrapper
from langchain_community.tools import ArxivQueryRun, WikipediaQueryRun, DuckDuckGoSearchRun
from langchain.agents import initialize_agent, AgentType
from langchain.callbacks import StreamlitCallbackHandler
import os
from dotenv import load_dotenv

# Load API keys
load_dotenv()
groq_api_key = os.getenv("GROQ_API_KEY")

# Initialize LLM
llm = ChatGroq(groq_api_key=groq_api_key, model_name="Llama3-8b-8192", streaming=True)

# Setup API wrappers
arxiv_wrapper = ArxivAPIWrapper(top_k_results=1, doc_content_chars_max=200)
arxiv = ArxivQueryRun(api_wrapper=arxiv_wrapper)

api_wrapper = WikipediaAPIWrapper(top_k_results=1, doc_content_chars_max=200)
wiki = WikipediaQueryRun(api_wrapper=api_wrapper)

search = DuckDuckGoSearchRun(name="Search")

# Define tools
tools = [search, arxiv, wiki]

# Initialize agent
agent = initialize_agent(tools, llm, agent_type=AgentType.ZERO_SHOT_REACT_DESCRIPTION, verbose=True)
```

---

## Advantages 🏆

- **💪 Enhanced Productivity:** Rapid access to condensed, relevant information eliminates unnecessary research time.
- **🌐 Multi-Domain Knowledge:** Seamless integration of academic, general, and web-wide information sources.
- **📲 User-Friendly Interface:** Intuitive and interactive, suitable for all users, regardless of technical expertise.
- **⚛️ Customizable:** Modular design allows for easy expansion with additional tools and APIs.

---

## Problems Solved 🛠️

1. **🔄 Information Overload:** Filters out noise and delivers concise results.
2. **⏳ Time Constraints:** Significantly reduces the time spent on manual searches.
3. **🔒 Lack of Reliable Sources:** Focuses on credible platforms like ArXiv and Wikipedia.
4. **📊 Fragmented Discovery Process:** Combines multiple sources into a unified query system.

---

## Benefits 🌟

- **For Researchers:** Accelerates access to academic papers and related knowledge.
- **For Professionals:** Enables quick and reliable fact-checking.
- **For Students:** Simplifies complex topics with concise explanations.

---

## Features 🌐

- **Real-Time Response:** Instant answers to your queries.
- **Multi-Language Support:** Ability to handle queries in various languages.
- **Secure and Private:** Does not store user data, ensuring privacy.
- **Customizable Output:** Tailor responses to specific needs (e.g., detailed vs. summary). 

---

## Future Enhancements 🌍

1. **Additional Integrations:**
   - Support for more specialized databases (e.g., PubMed, IEEE Xplore).
   - Integration with personal knowledge bases (e.g., Notion, Obsidian).

2. **Improved Query Understanding:**
   - Enhanced natural language processing for complex, multi-part queries.

3. **Custom Models:**
   - Fine-tuned models for domain-specific applications.

4. **Mobile Support:**
   - Develop mobile-friendly interfaces for on-the-go accessibility.

5. **User Customization:**
   - Options for users to prioritize certain sources or customize query results.

6. **Collaboration Features:**
   - Shared workspaces for team-based research.

---

## Getting Started 🚪

### Prerequisites:

- Python 3.8+
- Streamlit
- LangChain
- API keys for ChatGroq and other tools.

### Installation:

1. Clone the repository:
   ```bash
   git clone https://github.com/thatritikpatel/Brainwave-Insight-Search-Chat-and-Discover.git
   cd brainwave-insight-search
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Run the application:
   ```bash
   streamlit run app.py
   ```

---

## License ✅

This project is open-source and available under the [MIT License](LICENSE).

---

## Contributing 🧱

I welcome contributions! Please read our [Contributing Guidelines](CONTRIBUTING.md) to get started.

- Report bugs
- Suggest new features
- Submit pull requests

---

## Acknowledgments 💖

Special thanks to:

- The LangChain team for their robust framework.
- The Streamlit community for making app development simple.
- OpenAI and Groq for powering our language models.

---

## Feedback 🖊️

I value your feedback! Please share your thoughts via GitHub Issues or contact us directly. Let’s make Brainwave Insight Search even better together!

---

## 📧 Contact

For any queries or suggestions, feel free to reach out at 

- Ritik Patel - [https://www.linkedin.com/in/thatritikpatel/]
- Project Link: [https://github.com/thatritikpatel/Brainwave-Insight-Search-Chat-and-Discover]