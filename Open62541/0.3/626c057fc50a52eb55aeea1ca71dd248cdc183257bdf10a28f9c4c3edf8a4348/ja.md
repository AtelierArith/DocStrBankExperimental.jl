```
UA_Client_writeValueAttribute_scalar(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_DataType})
```

UAクライアントAPIを使用して、クライアント`client`を介してアクセスされるNodeId `nodeId`の属性Valueに値`new_val`を書き込みます。
