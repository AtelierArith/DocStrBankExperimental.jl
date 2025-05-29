```julia
DiscreteSymmetricBilinearForm(
    operators,
    FES;
    ...
) -> GradientRobustMultiPhysics.AssemblyPattern{SymmetricBilinearForm, Float64, ON_CELLS, _A, _B, GradientRobustMultiPhysics.NoAction} where {_A<:Real, _B<:Integer}
DiscreteSymmetricBilinearForm(
    operators,
    FES,
    action;
    T,
    AT,
    name,
    regions,
    apply_action_to
) -> GradientRobustMultiPhysics.AssemblyPattern{SymmetricBilinearForm, Float64, ON_CELLS}

```

Creates a (discrete) SymmetricBilinearForm assembly pattern. For more details see BilinearForm constructor.
