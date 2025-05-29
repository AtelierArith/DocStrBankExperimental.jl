```
UA_Client_writeWriteMaskAttribute(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_UInt32})
```

UAクライアントAPIを使用して、クライアント`client`を通じてアクセスされるNodeId `nodeId`の属性WriteMaskに値`new_val`を書き込みます。
