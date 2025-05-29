```
apply_local!(
    local_matrix::AbstractMatrix, local_vector::AbstractVector,
    global_dofs::AbstractVector, ch::ConstraintHandler;
    apply_zero::Bool = false
)
```

Similar to [`apply!`](@ref) but perform condensation of constrained degrees-of-freedom locally in `local_matrix` and `local_vector` *before* they are to be assembled into the global system.

When the keyword argument `apply_zero` is `true` all inhomogeneities are set to `0` (cf. [`apply!`](@ref) vs [`apply_zero!`](@ref)).

This method can only be used if all constraints are "local", i.e. no constraint couples with dofs outside of the element dofs (`global_dofs`) since condensation of such constraints requires writing to entries in the global matrix/vector. For such a case, [`apply_assemble!`](@ref) can be used instead.

Note that this method is destructive since it, by definition, modifies `local_matrix` and `local_vector`.
