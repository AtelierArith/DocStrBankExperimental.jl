```
@expansion(f, var, [var...])
```

Return a collection of (monomial, coefficient) tuples decomposing f into its consituent parts.

# Examples

```jldoctest
julia> using PolynomialRings

julia> R = @ring! ℤ[x,y];

julia> collect(@expand(x^3 + y^2, y))
2-element Array{Tuple{Tuple{Int16},@ring(ℤ[x])},1}:
 ((0,), x^3)
 ((2,), 1)

julia> collect(@expand(x^3 + y^2, x, y))
2-element Array{Tuple{Tuple{Int16,Int16},BigInt},1}:
 ((0, 2), 1)
 ((3, 0), 1)
```

# See also

`expansion(...)`, `@coefficient` and `coefficient`
