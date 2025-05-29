```
@expandcoefficients(f, vars...)
```

Return the coefficients of `f` when expanded as a polynomial in the given variables.

!!! note
    `vars` need to be literal variable names; it cannot be a variable containing it.


# Examples

```jldoctest
julia> using PolynomialRings

julia> R = @ring! ℤ[x,y];

julia> collect(@expandcoefficients(x^3 + y^2, y))
2-element Array{@ring(ℤ[x]),1}:
 x^3
 1

julia> collect(@expandcoefficients(x^3 + y^2, x, y))
2-element Array{BigInt,1}:
 1
 1
```

# See also

`expandcoefficients`, `@expansion`, `expansion`, `@coefficient` and `coefficient`
