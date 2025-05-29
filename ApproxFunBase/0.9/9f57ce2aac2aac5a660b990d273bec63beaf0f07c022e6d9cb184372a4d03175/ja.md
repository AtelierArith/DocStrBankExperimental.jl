```
ProductFun(M::AbstractVector{<:Fun{<:UnivariateSpace}}, sp::UnivariateSpace)
```

二変数関数 `f(x,y)` を `M` の一変数係数関数を用いて表現します。関数 `f` は次のように再構成できます。

$$
f\left(x,y\right)=\sum_{i}M_{i}\left(x\right)b_{i}\left(y\right),
$$

ここで $b_{i}\left(y\right)$ は空間 `sp` の $i$ 番目の基底関数を表します。

# 例

```jldoctest
julia> P = ProductFun([zeros(Chebyshev()), Fun(Chebyshev())], Chebyshev()); # corresponds to (x,y)->x*y

julia> P(0.1, 0.2) ≈ 0.1 * 0.2
true
```
