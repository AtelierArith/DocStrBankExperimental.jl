```
partial_transpose(X::AbstractMatrix, transp::AbstractVector, dims::AbstractVector = _equal_sizes(X))
```

行列 `X` の部分転置を、`transp` のサブシステムに対するサブシステム次元 `dims` で行います。引数 `dims` が省略された場合、2つの同じサイズのサブシステムが仮定されます。
