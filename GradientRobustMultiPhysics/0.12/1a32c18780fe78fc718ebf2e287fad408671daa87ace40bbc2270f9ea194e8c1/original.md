```julia
DiscreteLumpedBilinearForm(
    operators,
    FES;
    ...
) -> GradientRobustMultiPhysics.AssemblyPattern{LumpedBilinearForm, Float64, ON_CELLS, _A, _B, GradientRobustMultiPhysics.NoAction} where {_A<:Real, _B<:Integer}
DiscreteLumpedBilinearForm(
    operators,
    FES,
    action;
    T,
    AT,
    name,
    regions,
    apply_action_to
) -> GradientRobustMultiPhysics.AssemblyPattern{LumpedBilinearForm, Float64, ON_CELLS}

```

Creates a (discrete) LumpedBilinearForm assembly pattern. For more details see BilinearForm constructor.
