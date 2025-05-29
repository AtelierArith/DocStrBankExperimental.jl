```
on_message_reaction_remove_all!(
    f::Function
    c::Client
)
```

MESSAGE*REACTION*REMOVE_ALLゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります：

```
    (ctx::Context) -> Any 
```
