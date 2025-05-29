```julia
BilinearForm(
    operators_linear::Vector{DataType},
    operators_current::Vector{DataType},
    coeff_from::Vector{Int64},
    action::GradientRobustMultiPhysics.AbstractAction;
    name,
    AT,
    APT,
    apply_action_to,
    factor,
    regions,
    transposed_assembly,
    also_transposed_block,
    transpose_factor,
    store
) -> GradientRobustMultiPhysics.PDEOperator{Float64, BilinearForm, ON_CELLS}

```

generates a BilinearForm defined by the following arguments:

  * operators_linear  : operator for the two linear arguments (usually ansatz and test function)
  * operators_current : additional operators for other unknowns
  * coeff*from        : either PDE unknown ids or block ids for CurrentSolution given to assembly*operator! that should be used for operators_current
  * action            : tells how to further combine the operators*current+operator*ansatz evaluations (=input of action) to a result that is multiplied with the test function operator                     (if no action is specified, the full input vector is dot-producted with the test function operator evaluation)

Optional arguments:

  * apply*action*to   : specifies which of the two linear arguments is part of the action input ([1] = ansatz, [2] = test)
  * regions           : specifies in which regions the operator should assemble, default [0] means all regions
  * name              : name for this BilinearForm that is used in print messages
  * AT                : specifies on which entities of the grid the BilinearForm is assembled (default: ON_CELLS)
  * APT               : specifies the subtype of the APT_BilinearForm AssemblyPattern used for assembly (e.g. for lumping (wip))
  * factor            : additional factor that is multiplied during assembly
  * transposed_assembly : transposes the resulting assembled matrix (consider true here for non-symmetric operators)
  * also*transposed*block : when true toggles assembly of transposed system matrix block
  * transpose_factor  : factor for transposed block (default = factor)
  * store             : stores a matrix of the BilinearForm with the latest assembly result                     (e.g. when the operators sits in a system block that has to be reassembled in an iterative scheme)

Details on the action: The action is an Action consisting of a kernel function with interface (result, input, ...) and additional argument information. During assembly input will be filled with the operator evaluations of the other unknowns (i.e. operator*current, if specified) and appended to that the operator evaluation of one of the two linear argument (decided by apply*action_to). The result computed by the kernel function is multiplied (dot product) with the operator evaluation of the other linear argument. If no action is given, the assembly tries to multiply the operator evaluations (that would have been given as input) directly.
