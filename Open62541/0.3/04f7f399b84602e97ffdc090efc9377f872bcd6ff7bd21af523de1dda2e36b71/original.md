```
UA_Client_writeDataTypeAttribute(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_NodeId})
```

Uses the UA Client API to write the value `new_val` to the attribute DataType of the NodeId `nodeId` accessed through the client `client`. 
