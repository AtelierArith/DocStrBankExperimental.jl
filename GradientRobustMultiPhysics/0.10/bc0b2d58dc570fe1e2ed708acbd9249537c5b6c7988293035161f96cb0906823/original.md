```julia
LinearForm(operator_test::Type{<:??}; ...)
LinearForm(
    operator_test::Type{<:??},
    operators_current::Vector{DataType};
    ...
) -> GradientRobustMultiPhysics.PDEOperator{Float64, LinearForm, ON_CELLS}
LinearForm(
    operator_test::Type{<:??},
    operators_current::Vector{DataType},
    coeff_from::Vector{Int64};
    ...
) -> GradientRobustMultiPhysics.PDEOperator{Float64, LinearForm, ON_CELLS}
LinearForm(
    operator_test::Type{<:??},
    operators_current::Vector{DataType},
    coeff_from::Vector{Int64},
    action::GradientRobustMultiPhysics.AbstractAction;
    regions,
    name,
    AT,
    factor,
    store
) -> GradientRobustMultiPhysics.PDEOperator{Float64, LinearForm, ON_CELLS}

```

Creates a (PDE description level) LinearForm based on:

  * operator_test     : operator for the test function (assumes linearity for that part)
  * operators_current : additional operators for other unknowns
  * coeff*from        : either PDE unknown ids or block ids for CurrentSolution given to assembly*operator! that should be used for operators_current
  * action            : an Action with kernel of interface (result, input, kwargs) that takes input (= all but last operator evaluations) and computes result to be dot-producted with test function evaluation                     (if no action is specified, the full input vector is dot-producted with the test function operator evaluation)

Optional arguments:

  * regions: specifies in which regions the operator should assemble, default [0] means all regions
  * name : name for this LinearForm that is used in print messages
  * AT : specifies on which entities of the grid the LinearForm is assembled (default: ON_CELLS)
  * factor : additional factor that is multiplied during assembly
  * store : stores a vector of the LinearForm with the latest assembly result (e.g. when the operators sits in a system block that has to be reassembled in an iterative scheme)

Details on the action: The action is an Action consisting of a kernel function with interface (result, input, ...) and additional argument information. During assembly input will be filled with the operator evaluations of the other unknowns (i.e. operators*current). The result computed by the kernel function is multiplied (dot product) with the operator evaluation of the test function (i.e. operator*test). If no action is given, the assembly tries to multiply the operator evaluations (that would have been given as input) directly.
