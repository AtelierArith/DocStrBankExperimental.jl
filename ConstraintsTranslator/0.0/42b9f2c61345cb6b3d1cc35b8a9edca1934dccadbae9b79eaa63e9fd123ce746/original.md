```
GroqLLM
```

Structure encapsulating the parameters for accessing the Groq LLM API.

  * `api_key`: an API key for accessing the Groq API (https://groq.com), read from the environmental variable GROQ*API*KEY.
  * `model_id`: a string identifier for the model to query. See https://console.groq.com/docs/models for the list of available models.
  * `url`: URL for chat completions. Defaults to "https://api.groq.com/openai/v1/chat/completions".
