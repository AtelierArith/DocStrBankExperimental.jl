```
coefficients(cfs::AbstractVector, fromspace::Space, tospace::Space) -> Vector
```

Convert coefficients in `fromspace` to coefficients in `tospace`

# Examples

```jldoctest
julia> f = Fun(x->(3x^2-1)/2);

julia> coefficients(f, Chebyshev(), Legendre()) ≈ [0,0,1]
true

julia> g = Fun(x->(3x^2-1)/2, Legendre());

julia> coefficients(f, Chebyshev(), Legendre()) ≈ coefficients(g)
true
```
