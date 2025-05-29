```
EmbeddedOperator(
    subspace_operator::AbstractMatrix{<:Number},
    subsystem_indices::AbstractVector{Int},
    subspaces::AbstractVector{<:AbstractVector{Int}},
    subsystem_levels::AbstractVector{Int}
)
```

Embed the `subspace_operator` into the provided `subspaces` of a composite system, where the `subsystem_indices` list the subspaces at which the operator is defined, and the `subsystem_levels` list the levels of the subsystems in which the operator is embedded.
