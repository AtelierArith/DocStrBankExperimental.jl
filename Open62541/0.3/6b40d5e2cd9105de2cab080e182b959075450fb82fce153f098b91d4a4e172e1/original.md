```
UA_Client_writeInverseNameAttribute(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_LocalizedText})
```

Uses the UA Client API to write the value `new_val` to the attribute InverseName of the NodeId `nodeId` accessed through the client `client`. 
