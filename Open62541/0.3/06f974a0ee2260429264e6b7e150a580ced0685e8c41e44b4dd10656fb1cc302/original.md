```
UA_Client_writeBrowseNameAttribute_async(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, newValue::Ptr{UA_QualifiedName},
    callback::UA_ClientAsyncServiceCallback, userdata::Ptr{Cvoid},
    requestId::UInt32)::UA_StatusCode
```

Uses the asynchronous client API to write the value `newValue` to the attribute BrowseName  of the NodeId `nodeId` accessed through the client `client`. 
