```
UA_Client_writeBrowseNameAttribute(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_QualifiedName})
```

Uses the UA Client API to write the value `new_val` to the attribute BrowseName of the NodeId `nodeId` accessed through the client `client`. 
