```
UA_Client_writeBrowseNameAttribute(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_QualifiedName})
```

UAクライアントAPIを使用して、クライアント`client`を通じてアクセスされるNodeId `nodeId`の属性BrowseNameに値`new_val`を書き込みます。
