```julia
is_subset_basis(basis1, basis2)

```

Return a `Bool` indicating whether coefficients in `basis1` can be augmented to `basis2` with [`augment_coefficients`](@ref).

!!! note
    `true` does not mean that coefficients from `basis1` can just be padded with zeros, since they may be in different positions. Always use [`augment_coefficients`](@ref).

