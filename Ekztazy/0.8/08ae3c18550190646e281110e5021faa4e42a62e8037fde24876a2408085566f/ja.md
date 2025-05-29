```
component!(
    f::Function
    c::Client
    custom_id::AbstractString
    kwargs...
)
```

`custom_id` フィールドが `custom_id` と一致する InteractionData のための INTERACTION CREATE ゲートウェイイベントのハンドラーを追加します。`f` パラメータのシグネチャは次のようにする必要があります：

```
(ctx::Context) -> Any 
```
