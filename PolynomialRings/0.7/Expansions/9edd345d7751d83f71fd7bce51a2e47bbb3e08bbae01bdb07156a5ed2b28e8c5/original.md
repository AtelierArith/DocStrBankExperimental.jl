```
@linear_coefficient(f, vars...)
linear_coefficients(f, vars...)
```

Return the linear coefficients of `f` as a function of `vars`.

!!! note
    `vars` need to be symbols; e.g. they cannot be the polynomial `x`.


# Examples

```jldoctest
julia> using PolynomialRings

julia> R = @ring! ℤ[x,y];

julia> @linear_coefficients(x^3*y + x + y + 1, x)
1-element Array{@ring(ℤ[y]),1}:
 1

julia> @linear_coefficients(x^3*y + x + y + 1, x, y)
2-element Array{BigInt,1}:
 1
 1
```

# See also

`@constant_coefficient`, `@coefficient`, and `@expansion`
