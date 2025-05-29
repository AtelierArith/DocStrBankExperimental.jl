```
@polynomial_ring(R::Ring, varnames...; cached=true, internal_ordering=:lex)
```

Return polynomial ring from [`polynomial_ring(::Ring, ::Vararg)`](@ref) and introduce the generators into the current scope.

# Examples

```jldoctest
julia> S = @polynomial_ring(ZZ, "x#" => (1:2, 1:2), "y#" => 1:3)
Multivariate polynomial ring in 7 variables x11, x21, x12, x22, ..., y3
  over integers

julia> x11, x21, x12, x22
(x11, x21, x12, x22)

julia> y1, y2, y3
(y1, y2, y3)

julia> (S, [x11 x12; x21 x22], [y1, y2, y3]) == polynomial_ring(ZZ, "x#" => (1:2, 1:2), "y#" => 1:3)
true
```
