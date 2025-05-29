```
on_interaction_create!(
    f::Function
    c::Client
)
```

INTERACTION_CREATEゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります：

```
    (ctx::Context) -> Any 
```
