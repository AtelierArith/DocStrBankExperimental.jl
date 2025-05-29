```
on_channel_create!(
    f::Function
    c::Client
)
```

CHANNEL_CREATEゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります：

```
    (ctx::Context) -> Any 
```
