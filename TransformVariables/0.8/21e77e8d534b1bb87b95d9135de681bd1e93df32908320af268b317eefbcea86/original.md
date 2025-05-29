```julia
inverse!(x, transformation, y)

```

Put `inverse(t, y)` into a preallocated vector `x`, returning `x`.

Generalized indexing should be assumed on `x`.

See [`inverse_eltype`](@ref) for determining the type of `x`.
