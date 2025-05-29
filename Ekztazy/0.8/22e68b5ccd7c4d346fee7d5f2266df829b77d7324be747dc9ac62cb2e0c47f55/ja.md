```
on_message_delete_bulk!(
    f::Function
    c::Client
)
```

MESSAGE*DELETE*BULKゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります：

```
    (ctx::Context) -> Any 
```
