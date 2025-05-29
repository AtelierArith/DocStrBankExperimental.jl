```
response::Ptr{Open62541.UA_QueryNextResponse)} = UA_Client_Service_queryNext(client::Ptr{UA_Client}, request::Ptr{Open62541.UA_QueryNextResponse)})
```

Uses the client queryNext service API to deliver a `response` to a  previously defined `request`. Note that memory for the response is  allocated by C and needs to be cleaned up using  `UA_QueryNextResponse_delete(response)` after its use.

!!! This is a low-level function within open62541. It is normally  much better and more convenient to use a more specific, high level  function.              

See also:

[`Open62541.UA_QueryNextResponse`](@ref)

[`Open62541.UA_QueryNextRequest`](@ref)
