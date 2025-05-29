```
@coefficient(f, monomial)
```

Return a the coefficient of `f` at `monomial`.

!!! note
    `monomial` needs to be a literal monomial; it cannot be a variable containing a monomial.  This macro has a rather naive parser that gets exponents and variable names from `monomial`.

    This is considered a feature (not a bug) because it is only as a literal monomial that we can distinguish e.g. `x^4` from `x^4*y^0`.


# Examples

```jldoctest
julia> using PolynomialRings

julia> R = @ring! ℤ[x,y];

julia> @coefficient(x^3*y + x, x)
1

julia> @coefficient(x^3*y + x, x^3)
y

julia> @coefficient(x^3*y + x, x^3*y^0)
0

julia> @coefficient(x^3*y + x, x^3*y^1)
1
```

# See also

`coefficient`, `expansion` and `@expansion`
