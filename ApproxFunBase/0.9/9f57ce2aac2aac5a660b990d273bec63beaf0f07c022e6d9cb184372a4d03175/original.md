```
ProductFun(M::AbstractVector{<:Fun{<:UnivariateSpace}}, sp::UnivariateSpace)
```

Represent a bivariate function `f(x,y)` in terms of the univariate coefficient functions from `M`. The function `f` may be reconstructed as

$$
f\left(x,y\right)=\sum_{i}M_{i}\left(x\right)b_{i}\left(y\right),
$$

where $b_{i}\left(y\right)$ represents the $i$-th basis function for the space `sp`.

# Examples

```jldoctest
julia> P = ProductFun([zeros(Chebyshev()), Fun(Chebyshev())], Chebyshev()); # corresponds to (x,y)->x*y

julia> P(0.1, 0.2) ≈ 0.1 * 0.2
true
```
