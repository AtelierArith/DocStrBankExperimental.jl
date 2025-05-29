```
stop!(server::Server) -> Nothing
```

Stop a running MCP server.

# Arguments

  * `server::Server`: The server instance to stop

# Returns

  * `Nothing`: The function returns after setting the server to inactive

# Throws

  * `ServerError`: If the server is not currently running
