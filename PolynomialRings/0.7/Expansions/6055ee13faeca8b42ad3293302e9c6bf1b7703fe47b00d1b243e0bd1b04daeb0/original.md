```
@deg(f, vars...)
```

Return the total degree of `f` when expanded as a polynomial in the given variables.

!!! note
    `vars` need to be literal variable names; it cannot be a variable containing it.


# Examples

```jldoctest
julia> using PolynomialRings

julia> R = @ring! ℤ[x,y];

julia> @deg (x^2 + x*y - 1) x
2

julia> @deg (x^2 + x*y - 1) y
1
```

# See also

`deg`, `@expansion`
