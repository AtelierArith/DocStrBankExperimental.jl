```
request::Ptr{UA_CreateSubscriptionRequest} = UA_CreateSubscriptionRequest_default()
```

モニタリングアイテムを後で追加できるサブスクリプション作成リクエストを作成します。サブスクリプションのプロパティはデフォルト値に設定されています。

レスポンスのメモリはCによって割り当てられ、使用後に`UA_CreateSubscriptionRequest_delete(request)`を使用してクリーンアップする必要があります。

参照：

[`UA_CreateSubscriptionRequest`](@ref)
