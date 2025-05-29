```
gaussjacobi(n::Integer, α::Real, β::Real) -> x, w  # ノード、重み
```

指数 `α` と `β` の [ガウス-ジャコビ法](https://en.wikipedia.org/wiki/Gauss%E2%80%93Jacobi_quadrature) のノード `x` と重み `w` を返します。

$$
\int_{-1}^{1} f(x) (1-x)^\alpha(1+x)^\beta dx \approx \sum_{i=1}^{n} w_i f(x_i)
$$

# 例

```jldoctest
julia> x, w = gaussjacobi(3, 1/3, -1/3);

julia> f(x) = x^4;

julia> I = dot(w, f.(x));

julia> I ≈ 268π/729(√3)
true
```
