
**1. Introduction**
![Alt text]([elative/path/to/image.png](https://github.com/prabal-17/AI-Web-Scraping-with-Ollama/blob/main/llama.png))

The AI Web Scraper is a Streamlit-based application that allows users to scrape content from websites and extract specific information using AI-powered parsing. This report provides a comprehensive overview of the application's architecture, components, and functionality.

**2. Application Structure**

The application consists of three main Python files:

- **main.py**: The main Streamlit application
- **scrape.py**: Contains functions for web scraping
- **parse.py**: Handles the AI-powered parsing of scraped content

**2.1 Main Application (main.py)**

The main application file sets up the Streamlit user interface and orchestrates the web scraping and parsing processes.

**Key Components:**

- Streamlit UI setup
- Background image setting
- User input handling
- Web scraping initiation
- Parsed content display

**2.2 Web Scraping Module (scrape.py)**

This module is responsible for scraping web content using the Safari WebDriver and BeautifulSoup.

**Key Functions:**

- `scrape_website(website)`: Launches the Safari browser and fetches the HTML content of the specified website.
- `extract_body_content(html_content)`: Extracts the body content from the HTML.
- `clean_body_content(body_content)`: Removes scripts, styles, and unnecessary whitespace from the content.
- `split_dom_content(dom_content, max_length=6000)`: Splits the content into manageable chunks.

**Enabling the Safari Driver:**

To use the Safari WebDriver, ensure that the "Allow Remote Automation" option is enabled in Safari. This can be done by executing the following command in the terminal:

```bash
safaridriver --enable
```

**2.3 Parsing Module (parse.py)**

This module handles the AI-powered parsing of the scraped content using the Ollama language model.

**Key Components:**

- OllamaLLM initialization
- ChatPromptTemplate for instruction formatting
- `parse_with_ollama(dom_chunks, parse_description)`: Processes content chunks and extracts relevant information.

**3. Workflow**

- **User Input**: The user enters a URL and a description of the information they want to extract.
- **Web Scraping**: The application uses Safari to load the webpage and retrieve its HTML content.
- **Content Preparation**: The cleaned content is split into manageable chunks.
- **AI Parsing**: Each chunk is processed by the Ollama language model.
- **Result Display**: The parsed information is displayed to the user in the Streamlit interface.

**4. Key Technologies**

**4.1 Streamlit**

Streamlit is an open-source Python library used for creating web applications with minimal effort. It's particularly well-suited for data science and machine learning projects.

**Key Features:**

- Rapid prototyping and development of web applications
- Built-in support for data visualization and user input widgets
- Automatic rerun on code changes for quick iteration
- Easy deployment options

**Usage in the Project**: Streamlit is used to create the entire user interface of the AI Web Scraper. It handles the layout, user input fields, buttons, and display of results.

**4.2 Selenium**

Selenium is a powerful tool for automating web browsers. It's widely used for web testing but is also excellent for web scraping tasks, especially when dealing with dynamic content.

**Key Features:**

- Supports multiple browsers (Chrome, Firefox, Safari, etc.)
- Can interact with web elements (clicking buttons, filling forms)
- Waits for page loads and elements to appear
- Executes JavaScript for enhanced interaction

**Usage in the Project**: In the scrape.py file, Selenium is used to launch the Safari browser, navigate to the specified URL, and retrieve the page's HTML content.

**4.3 BeautifulSoup**

BeautifulSoup is a Python library for pulling data out of HTML and XML files. It creates a parse tree from page source code that can be used to extract data in a hierarchical and intuitive way.

**Key Features:**

- Navigates parse trees with Python-like idioms
- Supports multiple parsers for flexibility
- Handles poorly formatted markup effectively
- Provides simple methods to find and modify parse tree elements

**Usage in the Project**: BeautifulSoup is used in the scrape.py file to parse and clean the HTML content retrieved by Selenium.

**4.4 Ollama**

Ollama is an AI language model designed to run large language models locally. It provides an API for integrating these models into applications.

**Key Features:**

- Runs language models locally for privacy and speed
- Supports multiple models (e.g., Llama 2)
- Provides a simple API for text generation and completion
- Allows for fine-tuning and customization of models

**Usage in the Project**: In the parse.py file, Ollama is used through the OllamaLLM class from Langchain. It's initialized with the "llama3.2" model and used to process the scraped content chunks.

**4.5 Langchain**

Langchain is a framework for developing applications powered by language models. It provides tools to integrate AI models with other sources of computation or knowledge.

**Key Features:**

- Offers pre-built chains for common language model use-cases
- Provides prompts and prompt templates for consistent interactions
- Integrates with various language models and tools
- Facilitates memory management for conversational applications

**Usage in the Project**: Langchain is used in the parse.py file to create a processing chain. The ChatPromptTemplate is used to format instructions for the Ollama model.

**5. User Interface**

The application features a sleek, dark-themed interface with the following elements:

- Title and description
- URL input field
- "Scrape Website" button
- Expandable section to view raw scraped content
- Text area for entering parsing instructions
- "Parse Content" button
- Results display area

**6. AI Parsing Process**

- A template is used to format instructions for the AI model.
- The Ollama model processes each content chunk separately.
- The model extracts only the information that matches the user's description.
- Empty strings are returned if no matching information is found.
- Results from all chunks are combined and displayed to the user.

**7. Error Handling and Performance Optimization**

- The application includes error handling for invalid URLs and empty parsing descriptions.
- Content is split into chunks to handle large websites efficiently.
- A pure Python implementation of Protocol Buffers is used to mitigate potential browser-related errors.

**8. Potential Improvements**

- Implement multi-threading for faster processing of large websites.
- Add support for more complex scraping scenarios (e.g., JavaScript-rendered content).
- Incorporate a caching mechanism to reduce repeated scraping of the same URLs.
- Enhance the UI with progress bars and more detailed status updates.
- Implement error handling for network issues and timeouts.

**9. Conclusion**

The AI Web Scraper demonstrates an innovative approach to web content extraction by combining traditional web scraping techniques with AI-powered parsing. This application showcases the potential of AI in automating and enhancing web data extraction tasks, offering users a flexible and intelligent tool for gathering specific information from websites.

