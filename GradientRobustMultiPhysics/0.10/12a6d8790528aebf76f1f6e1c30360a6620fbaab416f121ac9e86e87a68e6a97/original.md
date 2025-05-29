```julia
LinearForm(
    operator::Type{<:??},
    f::GradientRobustMultiPhysics.AbstractUserDataType;
    name,
    kwargs...
) -> GradientRobustMultiPhysics.PDEOperator{Float64, LinearForm, ON_CELLS}

```

generates a LinearForm L(v) = (f,operator(v)) from a DataFunction

  * operator : operator applied to test function
  * action   : DataFunction, evaluation is multiplied with test function operator

Optional arguments:

  * regions           : specifies in which regions the operator should assemble, default [0] means all regions
  * name              : name for this LinearForm that is used in print messages
  * AT                : specifies on which entities of the grid the LinearForm is assembled (default: ON_CELLS)
  * factor            : additional factor that is multiplied during assembly
  * store             : stores a vector of the discretised LinearForm with the latest assembly result
