```
UA_Server_writeAccessLevel(server::Ptr{UA_Server}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_Byte})
```

サーバーAPIを使用して、`server`上のNodeId `nodeId`の属性AccessLevelに値`new_val`を書き込みます。
