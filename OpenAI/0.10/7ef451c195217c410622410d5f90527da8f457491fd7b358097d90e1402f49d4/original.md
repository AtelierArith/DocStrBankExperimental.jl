```
Update assistant
```

assistants = list*assistants(     api*key,     limit=2,     )

# Arguments

  * `api_key::String`: OpenAI API key
  * `assistant_id::String`: Assistant id (e.g. "asst_i1MDikQGNk2PJGtltQljCI6X")

# Keyword Arguments

  * `model_id::String`: Optional. The model ID to use for the assistant.
  * `name::String`: Optional. The name of the assistant.
  * `description::String`: Optional. The description of the assistant.
  * `instructions::String`: Optional. The instructions for the assistant.
  * `tools::Vector`: Optional. The tools for the assistant. May include `code_interpreter`, `retrieval`, or `function`.
  * `file_ids::Vector`: Optional. The file IDs that are attached to the assistant.
  * `metadata::Dict`: Optional. The metadata for the assistant. This is used primarily for record keeping. Up to 16 key-value pairs can be included in the metadata. Keys can be up to 64 characters long and values can be a maximum of 512 characters long.
  * `http_kwargs::NamedTuple`: Optional. Keyword arguments to pass to HTTP.request.

For more details about the endpoint, visit [https://platform.openai.com/docs/api-reference/assistants/modifyAssistant](https://platform.openai.com/docs/api-reference/assistants/modifyAssistant).

# Usage

```julia
assistant = modify_assistant(
    api_key,
    "asst_i1MDikQGNk2PJGtltQljCI6X",
    name="My Assistant, renamed",
)
```

should return something like

```
Main.OpenAI.OpenAIResponse{JSON3.Object{Vector{UInt8}, Vector{UInt64}}}(200, {
             "id": "asst_i1MDikQGNk2PJGtltQljCI6X",
         "object": "assistant",
     "created_at": 1701360630,
           "name": "My Assistant, renamed",
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
