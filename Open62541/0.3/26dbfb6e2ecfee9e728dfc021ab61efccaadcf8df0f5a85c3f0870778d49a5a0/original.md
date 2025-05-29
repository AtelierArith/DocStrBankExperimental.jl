```
UA_Client_writeWriteMaskAttribute(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_UInt32})
```

Uses the UA Client API to write the value `new_val` to the attribute WriteMask of the NodeId `nodeId` accessed through the client `client`. 
