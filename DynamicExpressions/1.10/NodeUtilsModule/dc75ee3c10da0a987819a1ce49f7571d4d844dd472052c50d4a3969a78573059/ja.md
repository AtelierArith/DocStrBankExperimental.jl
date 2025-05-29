```
set_scalar_constants!(tree::AbstractExpressionNode{T}, constants, refs) where {T}
```

ツリー内の定数を深さ優先順序で設定します。関数 `get_scalar_constants` は同じ順序でそれらを取得します。
