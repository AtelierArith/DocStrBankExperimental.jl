```
UA_Client_writeValueAttribute(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_Variant})
```

Uses the UA Client API to write the value `new_val` to the attribute Value of the NodeId `nodeId` accessed through the client `client`. 
