```
apply_assemble!(
    assembler::AbstractAssembler, ch::ConstraintHandler,
    global_dofs::AbstractVector{Int},
    local_matrix::AbstractMatrix, local_vector::AbstractVector;
    apply_zero::Bool = false
)
```

Assemble `local_matrix` and `local_vector` into the global system in `assembler` by first doing constraint condensation using [`apply_local!`](@ref).

This is similar to using [`apply_local!`](@ref) followed by [`assemble!`](@ref) with the advantage that non-local constraints can be handled, since this method can write to entries of the global matrix and vector outside of the indices in `global_dofs`.

When the keyword argument `apply_zero` is `true` all inhomogeneities are set to `0` (cf. [`apply!`](@ref) vs [`apply_zero!`](@ref)).

Note that this method is destructive since it modifies `local_matrix` and `local_vector`.
