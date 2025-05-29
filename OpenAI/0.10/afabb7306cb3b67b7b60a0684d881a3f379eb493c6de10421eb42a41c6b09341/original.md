```
Get assistant
```

Returns an `OpenAIResponse` object for a specific assistant.

# Arguments:

  * `api_key::String`: OpenAI API key
  * `assistant_id::String`: Assistant id (e.g. "asst_i1MDikQGNk2PJGtltQljCI6X")

# Keyword Arguments:

  * `http_kwargs::NamedTuple`: Optional. Keyword arguments to pass to HTTP.request.

For more details about the endpoint, visit [https://platform.openai.com/docs/api-reference/assistants/getAssistant](https://platform.openai.com/docs/api-reference/assistants/getAssistant).

# Usage

```julia
assistant = get_assistant(
    api_key,
    "asst_i1MDikQGNk2PJGtltQljCI6X"
)
```

should return something like

```
Main.OpenAI.OpenAIResponse{JSON3.Object{Vector{UInt8}, Vector{UInt64}}}(200, {
             "id": "asst_i1MDikQGNk2PJGtltQljCI6X",
         "object": "assistant",
     "created_at": 1701360630,
           "name": "My Assistant",
    "description": "My first assistant",
          "model": "gpt-3.5-turbo-1106",
   "instructions": "This is my first assistant",
          "tools": [],
       "file_ids": [],
       "metadata": {
                      "key2": "value2",
                      "key1": "value1"
                   }
})
```
