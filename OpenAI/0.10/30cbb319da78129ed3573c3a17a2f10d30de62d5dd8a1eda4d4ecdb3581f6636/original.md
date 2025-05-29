Create embeddings

# Arguments:

  * `api_key::String`: OpenAI API key
  * `input`: The input text to generate the embedding(s) for, as String or array of tokens.   To get embeddings for multiple inputs in a single request, pass an array of strings       or array of token arrays. Each input must not exceed 8192 tokens in length.       - `model_id::String`: Model id. Defaults to text-embedding-ada-002.

    ```
      # Keyword Arguments:
      - `http_kwargs::NamedTuple`: Optional. Keyword arguments to pass to HTTP.request.

      For additional details about the endpoint, visit <https://platform.openai.com/docs/api-reference/embeddings>
    ```
