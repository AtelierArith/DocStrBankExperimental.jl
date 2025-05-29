```
Create thread

POST https://api.openai.com/v1/threads
```

# Arguments:

  * `api_key::String`: OpenAI API key
  * `messages::Vector`: A list of messages to create the thread with.  Messages are dictionaries with the following fields: 

      * `role`: The role of the message. Currently only `user` is supported.
      * `content`: The content of the message.
      * `file_ids`: Optional. A list of file IDs to attach to the message.
      * `metadata`: Optional. Metadata for the message.

# Keyword Arguments:

  * `http_kwargs::NamedTuple`: Optional. Keyword arguments to pass to HTTP.request.'

# Usage

```julia
thread_id = create_thread(api_key, [
    Dict("role" => "user", "content" => "Hello, how are you?")
]).response.id
```
