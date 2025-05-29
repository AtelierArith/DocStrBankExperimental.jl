```
UA_Client_writeValueAttribute_async(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, newValue::Ptr{UA_Variant},
    callback::UA_ClientAsyncWriteCallback, userdata::Ptr{Cvoid},
    requestId::UInt32)::UA_StatusCode
```

Uses the asynchronous client API to write the value `newValue` to the attribute Value  of the NodeId `nodeId` accessed through the client `client`. 
