```
UA_Server_writeBrowseName(server::Ptr{UA_Server}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_QualifiedName})
```

サーバーAPIを使用して、`server`上のNodeId `nodeId`の属性BrowseNameに値`new_val`を書き込みます。
