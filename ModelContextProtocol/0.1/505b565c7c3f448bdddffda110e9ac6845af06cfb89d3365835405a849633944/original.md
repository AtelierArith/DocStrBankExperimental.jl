```
unsubscribe!(server::Server, uri::String, callback::Function) -> Server
```

Remove a subscription for a specific resource URI and callback function.

# Arguments

  * `server::Server`: The server instance
  * `uri::String`: The resource URI to unsubscribe from
  * `callback::Function`: The callback function to remove

# Returns

  * `Server`: The server instance for method chaining
