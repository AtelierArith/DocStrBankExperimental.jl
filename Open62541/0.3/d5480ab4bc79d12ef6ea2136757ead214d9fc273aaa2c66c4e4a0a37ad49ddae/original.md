```
UA_Client_writeMinimumSamplingIntervalAttribute(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_Double})
```

Uses the UA Client API to write the value `new_val` to the attribute MinimumSamplingInterval of the NodeId `nodeId` accessed through the client `client`. 
