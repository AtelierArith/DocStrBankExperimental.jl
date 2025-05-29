```
Page
```

Represents a browser page/tab with its associated WebSocket client.

# Fields

  * `client::WSClient`: The WebSocket client for communication
  * `target_id::String`: The unique identifier for this page/tab
  * `extras::Dict{String, Any}`: Additional page metadata refreshed on demand. It might be stale/inaccurate - run `update_page!` to refresh it.
