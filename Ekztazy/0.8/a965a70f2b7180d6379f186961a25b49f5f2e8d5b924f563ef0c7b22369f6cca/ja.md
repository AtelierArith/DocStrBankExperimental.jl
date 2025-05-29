```
on_message_create!(
    f::Function
    c::Client
)
```

MESSAGE_CREATEゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります：

```
    (ctx::Context) -> Any 
```
