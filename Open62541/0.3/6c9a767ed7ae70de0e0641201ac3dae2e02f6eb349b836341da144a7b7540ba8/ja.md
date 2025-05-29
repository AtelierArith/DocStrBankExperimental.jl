```
UA_Client_writeDescriptionAttribute(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_LocalizedText})
```

UAクライアントAPIを使用して、クライアント`client`を介してアクセスされるNodeId `nodeId`の属性Descriptionに値`new_val`を書き込みます。
