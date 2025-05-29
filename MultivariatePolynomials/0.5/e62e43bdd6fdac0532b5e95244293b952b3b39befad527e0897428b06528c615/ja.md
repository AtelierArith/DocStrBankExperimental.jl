```
sort_monomial_vector(X::AbstractVector{MT}) where {MT<:AbstractMonomialLike}
```

`σ`を返します。これは、`X`内のモノミアルをソートし、重複を排除するために必要な順序です。つまり、`(σ, X[σ])`を返します。

### 例

`sort_monomial_vector`を$[xy, x, xy, x^2y, x]$に呼び出すと、$([4, 1, 2], [x^2y, xy, x])$を返すべきです。
