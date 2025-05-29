```julia
LinearForm(
    operator::Type{<:??},
    action::GradientRobustMultiPhysics.AbstractAction;
    name,
    AT,
    regions,
    factor,
    store
) -> GradientRobustMultiPhysics.PDEOperator{Float64, LinearForm, ON_CELLS}

```

generates a LinearForm L(v) = (f,operator(v)) from an action

  * operator : operator applied to test function
  * action   : action that computes a result to be multiplied with test function operator

Optional arguments:

  * regions           : specifies in which regions the operator should assemble, default [0] means all regions
  * name              : name for this LinearForm that is used in print messages
  * AT                : specifies on which entities of the grid the LinearForm is assembled (default: ON_CELLS)
  * factor            : additional factor that is multiplied during assembly
  * store             : stores a vector of the discretised LinearForm with the latest assembly result

Details on the action: The action is an Action consisting of a kernel function with interface (result, input, ...) and additional argument information. During assembly input is ignored (only in this constructor for LinearForms). The result computed by the kernel function is multiplied (dot product) with the operator evaluation of the test function.
