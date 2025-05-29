```
has_capacity(n::Node)
```

ノード `n` が標準の容量を持っているかどうかを確認します。

デフォルトでは、[`Storage`](@ref) および [`Availability`](@ref) ノードは、複数の容量を持っている（`Storage`）か、持っていない（`Availability`）ため除外されます。
