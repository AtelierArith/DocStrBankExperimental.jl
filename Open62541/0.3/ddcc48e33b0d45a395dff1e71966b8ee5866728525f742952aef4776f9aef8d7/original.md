```
UA_Client_writeNodeClassAttribute(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_NodeClass})
```

Uses the UA Client API to write the value `new_val` to the attribute NodeClass of the NodeId `nodeId` accessed through the client `client`. 
