```
UA_Server_readBrowseName(server::Ptr{UA_Server}, nodeId::Ptr{UA_NodeId}, out::Ptr{UA_QualifiedName})
```

サーバーAPIを使用して、サーバー`server`上のNodeId `nodeId`から属性BrowseNameの値を読み取ります。結果は`out`に保存されます。

`out`のメモリは、この関数を使用する前にCによって割り当てられる必要があります。これは`out = UA_QualifiedName_new()`を使用して実行できます。結果のオブジェクトは、その使用後に`UA_QualifiedName_delete(out::Ptr{UA_QualifiedName})`を介してクリーンアップする必要があります。
