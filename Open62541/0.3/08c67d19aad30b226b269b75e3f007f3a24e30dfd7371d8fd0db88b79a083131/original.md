```
UA_Client_writeDisplayNameAttribute_async(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, newValue::Ptr{UA_LocalizedText},
    callback::UA_ClientAsyncServiceCallback, userdata::Ptr{Cvoid},
    requestId::UInt32)::UA_StatusCode
```

Uses the asynchronous client API to write the value `newValue` to the attribute DisplayName  of the NodeId `nodeId` accessed through the client `client`. 
