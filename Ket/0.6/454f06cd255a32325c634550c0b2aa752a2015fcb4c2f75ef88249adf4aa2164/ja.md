```
partial_transpose(X::AbstractMatrix, transp::Integer, dims::AbstractVector = _equal_sizes(X))
```

行列 `X` の部分転置を、部分系 `transp` に対して部分系の次元 `dims` で行います。引数 `dims` が省略された場合、2つの同じサイズの部分系が仮定されます。
