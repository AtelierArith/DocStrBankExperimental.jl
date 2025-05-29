```julia
DiscreteBilinearForm(
    operators,
    FES;
    ...
) -> GradientRobustMultiPhysics.AssemblyPattern{BilinearForm, Float64, ON_CELLS, _A, _B, GradientRobustMultiPhysics.NoAction} where {_A<:Real, _B<:Integer}
DiscreteBilinearForm(
    operators,
    FES,
    action;
    T,
    AT,
    name,
    regions,
    apply_action_to
) -> GradientRobustMultiPhysics.AssemblyPattern{BilinearForm, Float64, ON_CELLS}

```

Creates a (discrete) BilinearForm assembly pattern based on:

  * operators : operators that should be evaluated for the coressponding FESpace (last two refer to ansatz and test function)
  * FES       : FESpaces for each operator (last two refer to ansatz and test function)
  * action    : an Action with kernel of interface (result, input, kwargs) that takes input (= all but last operator evaluations) and computes result to be dot-producted with test function evaluation             (if no action is specified, the full input vector is dot-producted with the test function operator evaluation)

Optional arguments:

  * apply*action*to : specifies which of the two linear arguments is part of the action input ([1] = ansatz, [2] = test)
  * regions   : specifies in which regions the operator should assemble, default [0] means all regions
  * name      : name for this LinearForm that is used in print messages
  * AT        : specifies on which entities of the grid the LinearForm is assembled (default: ON_CELLS)
