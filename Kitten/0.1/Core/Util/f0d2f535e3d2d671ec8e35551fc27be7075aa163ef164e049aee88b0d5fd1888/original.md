```
format_sse_message(data::String; event::Union{String, Nothing} = nothing, id::Union{String, Nothing} = nothing)
```

Create a properly formatted Server-Sent Event (SSE) string.

# Arguments

  * `data`: The data to send. This should be a string. Newline characters in the data will be replaced with separate "data:" lines.
  * `event`: (optional) The type of event to send. If not provided, no event type will be sent. Should not contain newline characters.
  * `retry`: (optional) The reconnection time for the event in milliseconds. If not provided, no retry time will be sent. Should be an integer.
  * `id`: (optional) The ID of the event. If not provided, no ID will be sent. Should not contain newline characters.

# Notes

This function follows the Server-Sent Events (SSE) specification for sending events to the client.
