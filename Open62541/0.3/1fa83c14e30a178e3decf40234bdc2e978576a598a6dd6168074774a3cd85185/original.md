```
UA_Client_writeExecutableAttribute(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_Boolean})
```

Uses the UA Client API to write the value `new_val` to the attribute Executable of the NodeId `nodeId` accessed through the client `client`. 
