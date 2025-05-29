```
response::Ptr{Open62541.UA_RegisterNodesResponse)} = UA_Client_Service_registerNodes(client::Ptr{UA_Client}, request::Ptr{Open62541.UA_RegisterNodesResponse)})
```

Uses the client registerNodes service API to deliver a `response` to a  previously defined `request`. Note that memory for the response is  allocated by C and needs to be cleaned up using  `UA_RegisterNodesResponse_delete(response)` after its use.

!!! This is a low-level function within open62541. It is normally  much better and more convenient to use a more specific, high level  function.              

See also:

[`Open62541.UA_RegisterNodesResponse`](@ref)

[`Open62541.UA_RegisterNodesRequest`](@ref)
