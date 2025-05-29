```
WSClient
```

WebSocket client for Chrome DevTools Protocol communication.

# Fields

  * `ws::Union{WebSocket, Nothing}`: The WebSocket connection or nothing if not connected
  * `ws_url::String`: The WebSocket URL to connect to
  * `is_connected::Bool`: Connection status flag
  * `message_channel::Channel{Dict{String, Any}}`: Channel for message communication
  * `next_id::Int`: Counter for message IDs
  * `page_loaded::Bool`: Flag indicating if the page has finished loading
  * `endpoint::String`: The debugging endpoint URL
