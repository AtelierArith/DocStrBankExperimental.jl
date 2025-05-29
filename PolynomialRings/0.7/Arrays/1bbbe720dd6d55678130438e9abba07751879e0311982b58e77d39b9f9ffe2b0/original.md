```
flat_coefficients(a, symbol, [symbol...])
```

Return the *polynomial* coefficients of the *matrix* coefficients of `a`, when those matrix coefficients are regarded as polynomials in the given variables.

# Examples

```jldoctest
julia> using PolynomialRings

julia> R = @ring! ℤ[x,y];

julia> collect(flat_coefficients([x^3 + y^2; y^5], :y))
3-element Array{@ring(ℤ[x]),1}:
 1
 x^3
 1

julia> collect(flat_coefficients([x^3 + y^2, y^5], :x, :y))
3-element Array{BigInt,1}:
 1
 1
 1
```

# See also

`@expandcoefficients`, `@expansion`, `expansion`, `@coefficient` and `coefficient`
