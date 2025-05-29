```
select!(
    f::Function
    c::Client
    custom_id::AbstractString
    args::Vector{Tuple}
    kwargs...
)
```

INTERACTION CREATEゲートウェイイベントのハンドラーを追加します。ここで、InteractionDataの`custom_id`フィールドが`custom_id`と一致します。`f`パラメータのシグネチャは次のようにする必要があります。

```
(ctx::Context, choices::Vector{String}) -> Any 
```
