```
get_leakage_indices(subspace::AbstractVector{Int}, levels::Int)
get_leakage_indices(subspaces::AbstractVector{<:AbstractVector{Int}}, subsystem_levels::AbstractVector{Int})
get_leakage_indices(subsystem_levels::AbstractVector{Int}; subspace=1:2)
get_leakage_indices(op::EmbeddedOperator)
```

Get the indices for the states that are outside of the provided subspace of the quantum system.
