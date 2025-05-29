```
on_channel_delete!(
    f::Function
    c::Client
)
```

CHANNEL_DELETEゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります：

```
    (ctx::Context) -> Any 
```
