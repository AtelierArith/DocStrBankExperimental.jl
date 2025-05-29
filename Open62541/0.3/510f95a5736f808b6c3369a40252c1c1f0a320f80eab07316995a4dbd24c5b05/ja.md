```
UA_Client_writeValueAttribute(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_Variant})
```

UAクライアントAPIを使用して、クライアント`client`を通じてアクセスされるNodeId `nodeId`の属性Valueに値`new_val`を書き込みます。
