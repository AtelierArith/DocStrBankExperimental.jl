```
partial_trace(X::AbstractMatrix, remove::AbstractVector, dims::AbstractVector = _equal_sizes(X))
```

行列 `X` の部分トレースを、`remove` にあるサブシステムの次元 `dims` に対して計算します。引数 `dims` が省略された場合、2つの同じサイズのサブシステムが仮定されます。
