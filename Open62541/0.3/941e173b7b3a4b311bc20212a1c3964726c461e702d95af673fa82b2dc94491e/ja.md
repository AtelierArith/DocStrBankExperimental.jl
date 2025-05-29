```
UA_Client_writeAccessLevelAttribute(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_Byte})
```

UAクライアントAPIを使用して、クライアント`client`を通じてアクセスされたNodeId `nodeId`の属性AccessLevelに値`new_val`を書き込みます。
