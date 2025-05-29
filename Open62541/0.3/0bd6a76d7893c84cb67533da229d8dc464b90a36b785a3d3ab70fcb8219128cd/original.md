```
response::Ptr{Open62541.UA_AddReferencesResponse)} = UA_Client_Service_addReferences(client::Ptr{UA_Client}, request::Ptr{Open62541.UA_AddReferencesResponse)})
```

Uses the client addReferences service API to deliver a `response` to a  previously defined `request`. Note that memory for the response is  allocated by C and needs to be cleaned up using  `UA_AddReferencesResponse_delete(response)` after its use.

!!! This is a low-level function within open62541. It is normally  much better and more convenient to use a more specific, high level  function.              

See also:

[`Open62541.UA_AddReferencesResponse`](@ref)

[`Open62541.UA_AddReferencesRequest`](@ref)
