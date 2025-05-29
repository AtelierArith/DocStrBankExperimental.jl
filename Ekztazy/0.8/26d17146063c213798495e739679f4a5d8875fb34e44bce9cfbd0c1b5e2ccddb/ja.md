```
on_webhooks_update!(
    f::Function
    c::Client
)
```

WEBHOOKS_UPDATEゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります：

```
    (ctx::Context) -> Any 
```
