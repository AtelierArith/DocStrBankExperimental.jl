```
on_message_reaction_remove!(
    f::Function
    c::Client
)
```

MESSAGE*REACTION*REMOVEゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります：

```
    (ctx::Context) -> Any 
```
