# RegInSight ⚖️ AI Legislative Impact Forecaster

**RegInSight** is an AI-powered tool designed to provide an initial, rapid assessment of the potential impact of proposed legislation on existing laws. It helps legal professionals quickly identify potential interactions, conflicts, and overlaps, enabling them to focus their in-depth human review on the most critical areas.

This project was developed for the Legal Frontier Hackathon Project in Amsterdam.

## The Problem

When new legislation or regulations are proposed, legal professionals (legislative drafters, policy analysts, legal departments) face a complex and time-consuming task to identify how these new rules will impact the existing legal framework. Manually identifying all affected statutes, potential conflicts, or necessary amendments is prone to oversight and is resource-intensive.

## Our Solution: LexiCast

RegInSight offers a streamlined solution by leveraging the power of Google's Gemini AI model to perform a comparative textual analysis.

**Key Features:**

*   **Text Input:** Users paste the text of a new/proposed piece of legislation and relevant snippets from existing laws.
*   **AI-Powered Comparative Analysis:** Utilizes Google's Gemini AI model (`gemini-1.5-flash-preview-04-17`) for analysis.
*   **Impact Identification:** Identifies potential interactions, overlaps, direct modifications, or conflicts.
*   **Summarization:** Provides concise summaries of both the proposed legislation and the existing legal context.
*   **Key Phrase Highlighting:** Extracts key impactful phrases from the new legislation.
*   **Severity Assessment (Guess):** Offers a preliminary severity rating (High, Medium, Low, Informational) for each interaction.
*   **Structured Report Output:** Presents the analysis in a clear, structured report within a user-friendly web interface.

## Technology Stack

*   **Programming Language:** Python
*   **AI Model/API:** Google Gemini Pro (`gemini-1.5-flash-preview-04-17` model via `google-generativeai` SDK)
*   **AI Prompt Engineering & Testing:** Google AI Studio
*   **Web Application Framework:** Streamlit
*   **Development & Demo Environment:** Google Colaboratory (Colab)
*   **UI Exposure for Demo:** `pyngrok`
*   **Core Python Libraries:** `json`

## Running the Project (from the Colab Notebook)

The entire application (backend AI logic, Streamlit UI, and demo execution) is contained within the provided Google Colab notebook: `[Name_of_your_Colab_Notebook_File.ipynb]` (e.g., `lexicast_hackathon.ipynb`).

**Prerequisites:**

1.  A Google Account (for Google Colab and Google AI Studio/Gemini API).
2.  An Ngrok account and authtoken (for exposing the Streamlit app publicly from Colab).

**Steps to Run:**

1.  **Open the Notebook in Google Colab:**
    *   Upload the `[Name_of_your_Colab_Notebook_File.ipynb]` to your Google Drive and open it with Colab.
    *   Alternatively, if the repository is public, you can often open it directly in Colab from GitHub (File -> Open notebook -> GitHub -> paste repo URL).
2.  **Configure Secrets in Colab:**
    *   Click on the "Key" icon (Secrets) on the left sidebar of Colab.
    *   Add your **Google AI API Key**:
        *   Name: `GOOGLE_API_KEY`
        *   Value: `Your_Actual_Google_AI_API_Key`
    *   Add your **Ngrok Authtoken**:
        *   Name: `NGROK_AUTHTOKEN`
        *   Value: `Your_Actual_Ngrok_Authtoken`
    *   Ensure "Notebook access" is enabled for both secrets.
3.  **Run the Colab Cells Sequentially:**
    *   **Cell 1:** Installs necessary Python packages (`google-generativeai`, `streamlit`, `pyngrok`).
    *   **Cell 2:** Configures the Google Gemini API key. Verify it prints "Gemini API Key configured successfully!" and "Successfully instantiated model...".
    *   **Cell 3:** Defines the master prompt template and default legislative text snippets.
    *   **Cell 4:** Defines the core Python function for AI analysis.
    *   **Cell 5:** Tests the analysis function (optional for just running the app, but good for verification).
    *   **Cell 6 (`%%writefile app.py`):** Writes the Streamlit application code to an `app.py` file in the Colab environment. **Run this cell.**
    *   **Cell 7:** Sets the `GOOGLE_API_KEY_STREAMLIT` environment variable (necessary for the Streamlit process to access the API key). **Run this cell.**
    *   **Cell 8:** Starts the Streamlit application and creates a public `ngrok` tunnel. It will output a URL (e.g., `https://xxxx.ngrok-free.app`). **Run this cell.**
4.  **Access LexiCast:**
    *   Click the `ngrok` URL provided by Cell 8 to open the LexiCast application in your browser.
    *   The app will have sample texts pre-loaded. Click "Analyze Impact" to see it in action, or paste your own legislative texts.

## Future Plans

RegInSight has significant potential for future development:

*   Integration with live legal databases (e.g., EUR-Lex).
*   Advanced conflict detection using vector search and embeddings.
*   Version control for legislation and historical impact tracking.
*   Allowing user-defined internal policies for checking against external laws.
*   Enhanced UI/UX with more sophisticated visualizations and collaboration features.
*   Jurisdictional expansion and deeper AI analytical capabilities.

## Disclaimer

This is a hackathon project developed in a very short timeframe. The AI-generated analysis is for informational and illustrative purposes only and does not constitute legal advice. Always consult with qualified legal professionals for any legal matters.
