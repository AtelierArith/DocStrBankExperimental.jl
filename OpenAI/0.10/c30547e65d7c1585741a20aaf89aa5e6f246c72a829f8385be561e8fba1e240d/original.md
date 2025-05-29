```
List assistants
```

Returns an `OpenAIResponse` object containing a list of assistants, sorted by the `created_at` timestamp of the objects.

# Arguments:

  * `api_key::String`: OpenAI API key

# Keyword Arguments:

  * `limit::Integer` (optional): The maximum number of assistants to return.  Defaults to 20, must be between 1 and 100.
  * `order::String` (optional): The order to list the assistants in,  may be `asc` or `desc`. Defaults to `desc` (newest first).
  * `after` (optional): A cursor for use in pagination. `after` is an object ID that defines your place in the list.  For instance, if you make a list request and receive 100 objects,  ending with `obj_foo`, your subsequent call can include `after=obj_foo`  in order to fetch the next page of the list.
  * `before` (optional): A cursor for use in pagination. `before` is an object ID that defines your place in the list.  For instance, if you make a list request and receive 100 objects,  starting with `obj_bar`, your subsequent call can include `before=obj_bar`  in order to fetch the previous page of the list.
  * `http_kwargs::NamedTuple`: Optional. Keyword arguments to pass to HTTP.request.

For more details about the endpoint, visit [https://platform.openai.com/docs/api-reference/assistants/listAssistants](https://platform.openai.com/docs/api-reference/assistants/listAssistants).

# Usage

```julia
assistants = list_assistants(
    api_key,
    limit=2,
)
```

should return something like

```
Main.OpenAI.OpenAIResponse{JSON3.Object{Vector{UInt8}, Vector{UInt64}}}(200, {
     "object": "list",
       "data": [
                 {
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
                 }
               ],
   "first_id": "asst_i1MDikQGNk2PJGtltQljCI6X",
    "last_id": "asst_i1MDikQGNk2PJGtltQljCI6X",
   "has_more": false
})
```
