```
on_message_delete!(
    f::Function
    c::Client
)
```

MESSAGE_DELETEゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります：

```
    (ctx::Context) -> Any 
```
