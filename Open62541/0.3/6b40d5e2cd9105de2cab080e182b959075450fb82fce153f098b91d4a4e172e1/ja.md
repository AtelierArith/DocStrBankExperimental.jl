```
UA_Client_writeInverseNameAttribute(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_LocalizedText})
```

UAクライアントAPIを使用して、クライアント`client`を通じてアクセスされるNodeId `nodeId`の属性InverseNameに値`new_val`を書き込みます。
