```
EmbeddedOperator(
    subspace_operator::AbstractMatrix{<:Number},
    subsystem_indices::AbstractVector{Int},
    subspaces::AbstractVector{<:AbstractVector{Int}},
    composite_system::CompositeQuantumSystem
)
```

Embed the `subspace_operator` into the provided `subspaces` of a composite system.
