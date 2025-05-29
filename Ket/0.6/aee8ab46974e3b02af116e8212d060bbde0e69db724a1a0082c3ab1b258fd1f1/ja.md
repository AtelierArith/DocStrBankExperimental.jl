```
trace_replace(X::AbstractMatrix, remove::Integer, dims::AbstractVector = _equal_sizes(X))
```

行列 `X` の部分トレースを、サブシステム `remove` に対してサブシステムの次元 `dims` で取り、正規化された単位行列で置き換えます。引数 `dims` が省略された場合、同じサイズの2つのサブシステムが仮定されます。
