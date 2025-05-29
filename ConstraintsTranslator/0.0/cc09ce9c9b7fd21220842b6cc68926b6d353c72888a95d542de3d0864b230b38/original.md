```
Google LLM
```

Structure encapsulating the parameters for accessing the Google LLM API.

  * `api_key`: an API key for accessing the Google Gemini API (`https://ai.google.dev/gemini-api/docs/`), read from the environmental variable `GOOGLE_API_KEY`.
  * `model_id`: a string identifier for the model to query. See `https://ai.google.dev/gemini-api/docs/models/gemini` for the list of available models.
  * `url`: URL for chat completions. Defaults to `https://generativelanguage.googleapis.com/v1beta/models/{{model_id}}`.
