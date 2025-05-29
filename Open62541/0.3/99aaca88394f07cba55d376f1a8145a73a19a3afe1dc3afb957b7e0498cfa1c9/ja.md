```
UA_Client_readBrowseNameAttribute(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, out::Ptr{UA_QualifiedName})
```

UAクライアントAPIを使用して、クライアント`client`を通じてアクセスされるNodeId `nodeId`から属性BrowseNameの値を読み取ります。
