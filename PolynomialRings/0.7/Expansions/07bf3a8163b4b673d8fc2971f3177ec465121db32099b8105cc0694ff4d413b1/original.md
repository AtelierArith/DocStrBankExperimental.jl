```
expansion_terms(f, symbol, [symbol...])
```

Return the terms of `f` when expanded as a polynomial in the given variables.

# Examples

```jldoctest
julia> using PolynomialRings

julia> R = @ring! ℤ[x,y];

julia> collect(expansion_terms(x^3 + y^2 + 1, :y))
2-element Array{@ring(ℤ[x][y]),1}:
 x^3 + 1
 y^2

julia> collect(expansion_terms(x^3 + y^2 + 1, :x, :y))
3-element Array{@ring(ℤ[x,y]),1}:
 1
 y^2
 x^3
```

# See also

`@expandcoefficients`, `@expansion`, `expansion`, `@coefficient` and `coefficient`
