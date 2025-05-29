```
start!(server::Server) -> Nothing
```

Start the MCP server, setting up logging and entering the main server loop.

# Arguments

  * `server::Server`: The server instance to start

# Returns

  * `Nothing`: The function returns after the server stops

# Throws

  * `ServerError`: If the server is already running
