```
subscribe!(server::Server, uri::String, callback::Function) -> Server
```

Subscribe to updates for a specific resource identified by URI.

# Arguments

  * `server::Server`: The server instance
  * `uri::String`: The resource URI to subscribe to
  * `callback::Function`: The function to call when the resource is updated

# Returns

  * `Server`: The server instance for method chaining
