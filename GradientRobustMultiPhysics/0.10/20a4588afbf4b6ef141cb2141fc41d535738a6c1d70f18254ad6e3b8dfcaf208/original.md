```julia
NonlinearForm(
    operator_test::Type{<:??},
    operators_current::Vector{DataType},
    coeff_from::Vector{Int64},
    action_kernel,
    argsizes::Vector{Int64};
    name,
    AT,
    newton,
    sparse_jacobian,
    jacobian,
    dependencies,
    bonus_quadorder,
    store,
    factor,
    regions
) -> GradientRobustMultiPhysics.PDEOperator{Float64, NonlinearForm, ON_CELLS}

```

generates a NonlinearForm defined by the following arguments:

  * operator_test     : operator for the test function
  * operators_current : additional operators for other unknowns
  * coeff*from        : either PDE unknown ids or block ids for CurrentSolution given to assembly*operator! that should be used for operators_current
  * action_kernel     : function of interface (result, input, ...) that computes the nonlinear quantity that should be multiplied with the testfunction operator
  * argsizes          : dimensions of [result, input] of kernel function

Optional arguments:

  * dependencies      : code String for additional dependencies of the kernel/jacobians (substring of "XTI")
  * jacobian          : default = "auto" triggers automatic computation of jacobians by ForwardDiff, otherwise user can specify a function of interface (jacobian, input, ...) with matching dimensions and dependencies
  * sparse_jacobian   : use sparsity detection and sparse matrixes for local jacobians ?
  * regions           : specifies in which regions the operator should assemble, default [0] means all regions
  * name              : name for this NonlinearForm that is used in print messages
  * AT                : specifies on which entities of the grid the NonlinearForm is assembled (default: ON_CELLS)
  * factor            : additional factor that is multiplied during assembly
  * store             : stores a matrix of the discretised NonlinearForm with the latest assembly result
  * bonus_quadorder   : increases the quadrature order in assembly accordingly (additional to usual quadorder based on used FESpaces)

Some details: Given some operator G(u), the Newton iteration reads DG u_next = DG u - G(u) which is added to the rest of the (linear) operators in the PDEDescription. The local jacobians (= jacobians of the operator kernel) to build DG needed for this are computed by automatic differentation (ForwardDiff). The user can also specify a jacobian kernel function by hand (which may improve assembly times).

For default dependencies both the kernel functions for the operator and its jacobian have to satisfy the interface

```
function name(result,input,...)
```

where input is a vector of the operators of the solution and result is either what then is multiplied with operator2 of the testfunction (or the jacobian).
