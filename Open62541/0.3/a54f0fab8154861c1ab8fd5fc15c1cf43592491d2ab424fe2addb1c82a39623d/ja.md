```
UA_Client_writeValueRankAttribute(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_Int32})
```

UAクライアントAPIを使用して、クライアント`client`を介してアクセスされるNodeId `nodeId`の属性ValueRankに値`new_val`を書き込みます。
