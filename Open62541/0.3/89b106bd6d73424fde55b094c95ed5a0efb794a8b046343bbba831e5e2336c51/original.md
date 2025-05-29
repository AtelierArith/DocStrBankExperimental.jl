```
UA_Client_writeUserAccessLevelAttribute(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_Byte})
```

Uses the UA Client API to write the value `new_val` to the attribute UserAccessLevel of the NodeId `nodeId` accessed through the client `client`. 
