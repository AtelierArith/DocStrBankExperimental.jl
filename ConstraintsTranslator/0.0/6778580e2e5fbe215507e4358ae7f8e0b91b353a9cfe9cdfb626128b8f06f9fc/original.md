```
LlamaCppLLM
```

Structure encapsulating the parameters for accessing the llama.cpp server API.

  * `api_key`: an optional API key for accessing the server
  * `model_id`: a string identifier for the model to query. Unused, kept for API compatibility.
  * `url`: the URL of the llama.cpp server OpenAI API endpoint (e.g., http://localhost:8080)

NOTE: we do not apply the appropriate chat templates to the prompt. This must be handled either in an external code path or by the server.
