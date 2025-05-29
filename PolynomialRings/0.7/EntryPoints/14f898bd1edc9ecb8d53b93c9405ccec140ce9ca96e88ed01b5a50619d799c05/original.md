```
@polyvar var [var...]
```

Define a polynomial ring in the given variables, and inject them into the surrounding scope.

This is equivalent to `@ring! Int[var...]`.

If you need different coefficient rings, or need to specify a non-default monomial order or exponent integer type, use `@ring!` or `polynomial_ring` instead.

# Examples

```jldoctest
julia> using PolynomialRings

julia> @polyvar x y;

julia> x + 3y
x + 3*y

julia> @polyvar ε[];

julia> 1 + ε()*x + ε()*y
ε[1]*x + ε[2]*y + 1
```

# See also

`polynomial_ring` `@ring!`
