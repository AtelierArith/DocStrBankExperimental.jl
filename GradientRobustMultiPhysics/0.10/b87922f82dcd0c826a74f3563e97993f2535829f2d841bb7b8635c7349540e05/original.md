```julia
DiscreteLinearForm(
    operators,
    FES::Array{<:GradientRobustMultiPhysics.FESpace{Tv, Ti}, 1};
    ...
) -> GradientRobustMultiPhysics.AssemblyPattern{LinearForm, Float64, ON_CELLS, _A, _B, GradientRobustMultiPhysics.NoAction} where {_A<:Real, _B<:Integer}
DiscreteLinearForm(
    operators,
    FES::Array{<:GradientRobustMultiPhysics.FESpace{Tv, Ti}, 1},
    action;
    T,
    AT,
    regions,
    name
) -> GradientRobustMultiPhysics.AssemblyPattern{LinearForm, Float64, ON_CELLS}

```

Creates a (discrete) LinearForm assembly pattern based on:

  * operators : operators that should be evaluated for the coressponding FESpace (last one refers to test function)
  * FES       : FESpaces for each operator (last one refers to test function)
  * action    : an Action with kernel of interface (result, input, kwargs) that takes input (= all but last operator evaluations) and computes result to be dot-producted with test function evaluation             (if no action is specified, the full input vector is dot-producted with the test function operator evaluation)

Optional arguments:

  * regions   : specifies in which regions the operator should assemble, default [0] means all regions
  * name      : name for this LinearForm that is used in print messages
  * AT        : specifies on which entities of the grid the LinearForm is assembled (default: ON_CELLS)
