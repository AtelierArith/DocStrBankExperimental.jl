```
UA_Client_writeHistorizingAttribute(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_Boolean})
```

UAクライアントAPIを使用して、クライアント`client`を介してアクセスされるNodeId `nodeId`の属性Historizingに値`new_val`を書き込みます。
