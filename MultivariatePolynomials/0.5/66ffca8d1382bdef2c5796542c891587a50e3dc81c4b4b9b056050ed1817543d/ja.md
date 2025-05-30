```
merge_monomial_vectors{MT<:AbstractMonomialLike, MVT<:AbstractVector{MT}}(X::AbstractVector{MVT}}
```

`X`のエントリに含まれるモノミアルのベクトルを、重複なしで昇順に返します。すなわち、`monomial_vector(vcat(X...))`です。

### 例

$$
[[xy, x, xy], [x^2y, x]]
$$

に対して`merge_monomial_vectors`を呼び出すと、$[x^2y, xy, x]$が返されるべきです。
