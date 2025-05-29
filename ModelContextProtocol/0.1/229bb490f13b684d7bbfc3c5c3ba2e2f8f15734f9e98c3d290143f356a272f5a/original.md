```
parse_message(json::String) -> MCPMessage
```

Parse a JSON-RPC message string into the appropriate typed message object.

# Arguments

  * `json::String`: The raw JSON-RPC message string

# Returns

  * `MCPMessage`: A typed MCPMessage subtype (JSONRPCRequest, JSONRPCResponse, JSONRPCNotification, or JSONRPCError)
