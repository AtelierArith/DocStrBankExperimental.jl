```
monomial_vector(X::AbstractVector{MT}) where {MT<:AbstractMonomialLike}
```

重複なしで増加順に整列されたモノミアルのベクトル `X` を返します。

### 例

$$
[xy, x, xy, x^2y, x]
$$

に対して `monomial_vector` を呼び出すと、$[x^2y, xy, x]$ が返されるべきです。
