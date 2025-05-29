```
UA_Client_writeAccessLevelExAttribute(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_NodeId})
```

UAクライアントAPIを使用して、クライアント`client`を通じてアクセスされるNodeId `nodeId`の属性AccessLevelExに値`new_val`を書き込みます。
