```
HomogeneousPolynomial([T::Type=Float64], nv::Int])
```

`nv` 番目の独立した `HomogeneousPolynomial{T}` を定義するためのショートカット。`T` のデフォルト型は `Float64` です。

```julia
julia> HomogeneousPolynomial(1)
 1.0 x₁

julia> HomogeneousPolynomial(Rational{Int}, 2)
 1//1 x₂
```
