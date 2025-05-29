```
get_scalar_constants(tree::AbstractExpressionNode{T}, BT::Type = T)::Vector{T} where {T}
```

ツリー内のすべてのスカラー定数を深さ優先順序で取得します。関数 `set_scalar_constants!` は、この関数の出力に従って同じ順序でそれらを設定します。また、`set_scalar_constants!` 関数で使用されるメタデータも返します。
