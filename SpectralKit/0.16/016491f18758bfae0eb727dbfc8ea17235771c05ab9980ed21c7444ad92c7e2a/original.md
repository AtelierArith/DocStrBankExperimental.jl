`augment_coefficients(basis1, basis2, θ1)`

Return a set of coefficients `θ2` for `basis2` such that

```julia
linear_combination(basis1, θ1, x) == linear_combination(basis2, θ2, x)
```

for any `x` in the domain. In practice this means padding with zeros.

Throw a `ArgumentError` if the bases are incompatible with each other or `x`, or this is not possible. Methods may not be defined for incompatible bases, compatibility between bases can be checked with [`is_subset_basis`](@ref).
