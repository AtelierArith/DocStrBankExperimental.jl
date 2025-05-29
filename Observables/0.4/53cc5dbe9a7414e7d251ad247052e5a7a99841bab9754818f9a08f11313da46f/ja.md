```
obs = Observable(val)
obs = Observable{T}(val)
```

`Ref`のようですが、[`on`](@ref)や[`map`](@ref)を使用してハンドラーを追加することで、更新を監視できます。
