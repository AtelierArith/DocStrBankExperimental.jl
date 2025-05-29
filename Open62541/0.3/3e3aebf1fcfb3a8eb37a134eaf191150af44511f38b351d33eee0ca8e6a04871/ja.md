```
UA_Server_writeDataValue(server::Ptr{UA_Server}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_DataValue})
```

サーバーAPIを使用して、`server`上のNodeId `nodeId`の属性DataValueに値`new_val`を書き込みます。
