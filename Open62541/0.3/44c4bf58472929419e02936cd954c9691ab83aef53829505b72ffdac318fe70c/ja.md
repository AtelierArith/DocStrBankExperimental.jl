```
UA_Server_readMinimumSamplingInterval(server::Ptr{UA_Server}, nodeId::Ptr{UA_NodeId}, out::Ptr{UA_Double})
```

サーバーAPIを使用して、サーバー`server`上のNodeId `nodeId`から属性MinimumSamplingIntervalの値を読み取ります。結果は`out`に保存されます。

`out`のメモリは、この関数を使用する前にCによって割り当てられている必要があります。これは`out = UA_Double_new()`を使用して実行できます。結果のオブジェクトは、その使用後に`UA_Double_delete(out::Ptr{UA_Double})`を介してクリーンアップする必要があります。
