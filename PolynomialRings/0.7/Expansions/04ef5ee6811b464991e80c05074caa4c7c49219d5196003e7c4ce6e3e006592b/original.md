```
coefficient(f, exponent_tuple, symbol, [symbol...])
```

Return a the coefficient of f at monomial. In the REPL, you likely want to use the friendlier version `@coefficient`.

# Examples

```jldoctest
julia> using PolynomialRings

julia> R = @ring! ℤ[x,y];

julia> coefficient(x^3*y + x, (1,), :x)
1

julia> coefficient(x^3*y + x, (3,), :x)
y

julia> coefficient(x^3*y + x, (3,0), :x, :y)
0

julia> coefficient(x^3*y + x, (3,1), :x, :y)
1
```

# See also

`@coefficient`, `expansion` and `@expansion`
