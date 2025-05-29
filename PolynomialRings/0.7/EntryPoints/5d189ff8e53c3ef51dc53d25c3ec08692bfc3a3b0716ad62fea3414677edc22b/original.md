```
@ring! ℚ[x,y]
```

Define and return the specified polynomial ring, and bind the variable names to its generators.

Currently, the supported rings are: ℚ (`Rational{BigInt}`), ℤ (`BigInt`), ℝ (`BigFloat`) and ℂ (`Complex{BigFloat}`).

Note: `@ring!` returns the ring and injects the variables. The macro `@ring` only returns the ring.

If you need different coefficient rings, or need to specify a non-default monomial order or exponent integer type, use `polynomial_ring` instead.

# Examples

```jldoctest
julia> using PolynomialRings

julia> @ring! ℚ[x,y];

julia> x^3 + y
x^3 + y
```

# See also

`polynomial_ring`
