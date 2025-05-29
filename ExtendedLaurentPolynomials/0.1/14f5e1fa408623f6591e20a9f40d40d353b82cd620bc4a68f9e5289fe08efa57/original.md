```
Polynomial{T}(coeffs, exponent; variable)
```

Creates a Polynomial with `coeffs` of type `T`. Supports `Rational` exponents and substitution.

#Examples

```julia
julia> Polynomial(8)
8

julia> Polynomial([1, 2, 3, 4, 5], [-2, -1, 0, 1, 2])
z^-2 + 2*z^-1 + 3 + 4*z + 5*z^2

julia> Polynomial([1, 2, 3, 4, 5], [-2, -1, 0, 1, 2]; variable=:x)
x^-2 + 2*x^-1 + 3 + 4*x + 5*x^2

julia> Polynomial([1, 2, 3, 4, 5], [-2, -1, 0, 1, 2]; ϵ=10^(-3))
z^-2 + 2*z^-1 + 3 + 4*z + 5*z^2
```
