```
ImmutablePolynomial{T, X, N}(coeffs)
```

Construct an immutable (static) polynomial from its coefficients `a₀, a₁, …, aₙ`, lowest order first, optionally in terms of the given variable `x` where `x` can be a character, symbol, or string.

If $p = a_n x^n + \ldots + a_2 x^2 + a_1 x + a_0$, we construct this through `ImmutablePolynomial((a_0, a_1, ..., a_n))` (assuming `a_n ≠ 0`). As well, a vector or number can be used for construction.

The usual arithmetic operators are overloaded to work with polynomials as well as with combinations of polynomials and scalars. However, operations involving two non-constant polynomials of different variables causes an error. Unlike other polynomials, `setindex!` is not defined for `ImmutablePolynomials`.

As the degree of the polynomial (`+1`) is a compile-time constant, several performance improvements are possible. For example, immutable polynomials can take advantage of faster polynomial evaluation provided by `evalpoly` from Julia 1.4; similar methods are also used for addition and multiplication.

However, as the degree is included in the type, promotion between immutable polynomials can not promote to a common type. As such, they are precluded from use in rational functions.

!!! note
    `ImmutablePolynomial` is not axis-aware, and it treats `coeffs` simply as a list of coefficients with the first index always corresponding to the constant term.


# Examples

```jldoctest
julia> using Polynomials

julia> ImmutablePolynomial((1, 0, 3, 4))
ImmutablePolynomial(1 + 3*x^2 + 4*x^3)

julia> ImmutablePolynomial((1, 2, 3), :s)
ImmutablePolynomial(1 + 2*s + 3*s^2)

julia> one(ImmutablePolynomial)
ImmutablePolynomial(1.0)
```

!!! note
    This was modeled after [StaticUnivariatePolynomials](https://github.com/tkoolen/StaticUnivariatePolynomials.jl) by `@tkoolen`.

