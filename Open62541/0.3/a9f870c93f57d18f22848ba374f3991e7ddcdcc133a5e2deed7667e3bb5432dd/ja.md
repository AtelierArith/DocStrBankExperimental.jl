```
request::Ptr{UA_MonitoredItemCreateRequest} = UA_MonitoredItemCreateRequest_default(nodeId::Ptr{UA_NodeId})
```

`nodeId`を監視するモニタリングアイテム作成リクエストを作成します。モニタリングアイテムのプロパティはデフォルト値に設定されています。

リクエストのメモリはCによって割り当てられ、使用後は`UA_MonitoredItemCreateRequest_delete(request)`を使用してクリーンアップする必要があります。

参照：

[`UA_MonitoredItemCreateRequest`](@ref)
