```
UA_Client_writeUserWriteMaskAttribute(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_UInt32})
```

UAクライアントAPIを使用して、クライアント`client`を介してアクセスされるNodeId `nodeId`の属性UserWriteMaskに値`new_val`を書き込みます。
