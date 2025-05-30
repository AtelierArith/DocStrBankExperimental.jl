```
monomial_vector(a, X::AbstractVector{MT}) where {MT<:AbstractMonomialLike}
```

`b, Y`を返します。ここで、`Y`は重複なしで昇順に並べられた`X`のモノミアルのベクトルであり、`b`は`a`の対応する係数のベクトルで、重複するエントリの係数は合計されます。

### 例

$$
[2, 1, 4, 3, -1], [xy, x, xy, x^2y, x]
$$

に対して`monomial_vector`を呼び出すと、$[3, 6, 0], [x^2y, xy, x]$が返されるべきです。
