```
partial_trace(X::AbstractMatrix, remove::Integer, dims::AbstractVector = _equal_sizes(X)))
```

行列 `X` の部分トレースを、サブシステム `remove` に対するサブシステムの次元 `dims` で取得します。引数 `dims` が省略された場合、2つの同じサイズのサブシステムが仮定されます。
