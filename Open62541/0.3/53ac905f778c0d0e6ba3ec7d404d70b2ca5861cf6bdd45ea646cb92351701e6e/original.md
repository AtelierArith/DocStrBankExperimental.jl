```
JUA_Server_writeValue(server::JUA_Server, nodeId::JUA_NodeId, newvalue)::UA_StatusCode
```

uses the server API to write the value `newvalue` to `nodeId` on `server`. `new_value` must either be a `JUA_Variant` or a Julia value/array compatible with any of its constructors.

See also [`JUA_Variant`](@ref)
