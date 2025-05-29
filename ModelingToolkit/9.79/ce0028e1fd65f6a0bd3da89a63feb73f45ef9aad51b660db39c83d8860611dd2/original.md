```julia
substitute_component(
    sys::ModelingToolkit.AbstractSystem,
    rule::Pair{T<:ModelingToolkit.AbstractSystem, T<:ModelingToolkit.AbstractSystem}
) -> Any

```

Given a hierarchical system `sys` and a rule `lhs => rhs`, replace the subsystem `lhs` in `sys` by `rhs`. The `lhs` must be the namespaced version of a subsystem of `sys` (e.g. obtained via `sys.inner.component`). The `rhs` must be valid as per the following conditions:

1. `rhs` must not be namespaced.
2. The name of `rhs` must be the same as the unnamespaced name of `lhs`.
3. Neither one of `lhs` or `rhs` can be marked as complete.
4. Both `lhs` and `rhs` must share the same independent variable.
5. `rhs` must contain at least all of the unknowns and parameters present in `lhs`.
6. Corresponding unknowns in `rhs` must share the same connection and causality (input/output) metadata as their counterparts in `lhs`.
7. For each subsystem of `lhs`, there must be an identically named subsystem of `rhs`. These two corresponding subsystems must satisfy conditions 3, 4, 5, 6, 7. If the subsystem of `lhs` is a connector, the corresponding subsystem of `rhs` must also be a connector of the same type.

`sys` also cannot be marked as complete.
