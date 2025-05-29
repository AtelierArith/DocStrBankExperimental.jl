```
on_message_reaction_add!(
    f::Function
    c::Client
)
```

MESSAGE*REACTION*ADDゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります：

```
    (ctx::Context) -> Any 
```
