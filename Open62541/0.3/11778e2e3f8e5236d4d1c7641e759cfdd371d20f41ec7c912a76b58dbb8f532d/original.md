```
JUA_Client_writeValueAttribute(server::JUA_Client, nodeId::JUA_NodeId, newvalue)::UA_StatusCode
```

uses the client API to write the value `newvalue` to `nodeId` to the server that the `client` is connected to.

`new_value` must either be a `JUA_Variant` or a Julia value/array compatible with any of its constructors.

See also [`JUA_Variant`](@ref)
