```
HomogeneousPolynomial([T::Type=Float64], nv::Int])
```

Shortcut to define the `nv`-th independent `HomogeneousPolynomial{T}`. The default type for `T` is `Float64`.

```julia
julia> HomogeneousPolynomial(1)
 1.0 x₁

julia> HomogeneousPolynomial(Rational{Int}, 2)
 1//1 x₂
```
