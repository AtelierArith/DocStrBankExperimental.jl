```
Delete assistant
```

Delete an assistant by ID.

# Arguments:

  * `api_key::String`: OpenAI API key
  * `assistant_id::String`: Assistant id (e.g. "asst_i1MDikQGNk2PJGtltQljCI6X")

# Keyword Arguments:

  * `http_kwargs::NamedTuple`: Optional. Keyword arguments to pass to HTTP.request.

For more details about the endpoint, visit [https://platform.openai.com/docs/api-reference/assistants/deleteAssistant](https://platform.openai.com/docs/api-reference/assistants/deleteAssistant).

# Usage

```julia
# Create an assistant to delete
resp = create_assistant(
    api_key,
    "gpt-3.5-turbo-1106",
    name="My Assistant",
)
resp_id = resp.response.id

# Delete that assistant
delete_assistant(
    api_key,
    resp_id,
)
```

should return something like

```
Main.OpenAI.OpenAIResponse{JSON3.Object{Vector{UInt8}, Vector{UInt64}}}(200, {
        "id": "asst_15GkSjSnF5SzGpItO22L6JYI",
    "object": "assistant.deleted",
   "deleted": true
})
```
