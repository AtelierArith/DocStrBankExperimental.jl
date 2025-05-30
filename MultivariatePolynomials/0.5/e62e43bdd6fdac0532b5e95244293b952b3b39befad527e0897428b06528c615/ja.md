```
sort_monomial_vector(X::AbstractVector{MT}) where {MT<:AbstractMonomialLike}
```

返すのは `σ` で、これは `X` のモノミアルをソートし、重複をなくすために取るべき順序を示し、ソートされたモノミアルのベクトルを返します。つまり、`(σ, X[σ])` を返します。

### 例

`sort_monomial_vector` を $[xy, x, xy, x^2y, x]$ に呼び出すと、$([4, 1, 2], [x^2y, xy, x])$ を返すべきです。
