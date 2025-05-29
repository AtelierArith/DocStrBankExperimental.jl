```
expansion(f, symbol, [symbol...])
```

Return a collection of (monomial, coefficient) tuples decomposing f into its consituent parts.

In the REPL, you likely want to use the friendlier version `@expansion` instead.

# Examples

```jldoctest
julia> using PolynomialRings

julia> R = @ring! ℤ[x,y];

julia> collect(expansion(x^3 + y^2, :y))
2-element Array{(Term over @ring(ℤ[x]) in @degrevlex(y)),1}:
 x^3
 y^2

julia> collect(expansion(x^3 + y^2, :x, :y))
2-element Array{(Term over BigInt in @degrevlex(x > y)),1}:
 y^2
 x^3
```

# See also

`@expansion(...)`, `@coefficient` and `coefficient`
