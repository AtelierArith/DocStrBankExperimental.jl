```
UA_Client_writeNodeClassAttribute(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_NodeClass})
```

UAクライアントAPIを使用して、クライアント`client`を通じてアクセスされるNodeId `nodeId`の属性NodeClassに値`new_val`を書き込みます。
