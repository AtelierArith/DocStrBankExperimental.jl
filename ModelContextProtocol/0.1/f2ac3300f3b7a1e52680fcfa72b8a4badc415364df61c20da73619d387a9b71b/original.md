```
serialize_message(msg::MCPMessage) -> String
```

Serialize an MCP message object into a JSON-RPC compliant string.

# Arguments

  * `msg::MCPMessage`: The message object to serialize (Request, Response, Notification, or Error)

# Returns

  * `String`: A JSON string representation of the message following the JSON-RPC 2.0 specification
