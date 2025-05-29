```
is_identity(G::AbstractLieGroup, q; kwargs...)
```

Check whether `q` is the identity on the [`AbstractLieGroup`](@ref) $\mathcal G$. This means it is either the [`Identity`](@ref)`{O}` with the respect to the corresponding [`AbstractGroupOperation`](@ref) `O`, or (approximately) the correct point representation.

# See also

[`identity_element`](@ref), [`identity_element!`](@ref)
