```julia
ConvectionOperator(
    a_from::Int64,
    a_operator::Type{<:??},
    xdim::Int64,
    ncomponents::Int64;
    name,
    AT,
    a_to,
    factor,
    ansatz_operator,
    test_operator,
    regions,
    newton,
    store,
    transposed_assembly,
    bonus_quadorder
) -> Union{GradientRobustMultiPhysics.PDEOperator{Float64, BilinearForm, ON_CELLS}, GradientRobustMultiPhysics.PDEOperator{Float64, NonlinearForm, ON_CELLS}}

```

constructs a convection term of the form c(a,u,v) = (a*operator(a)*ansatz*operator(u),test_operator(v)) as a BilinearForm (or NonlinearForm, see newton argument)

  * a_from      : id of registered unknown to be used in the spot a
  * a_operator  : operator applied to a
  * xdim        : expected space dimension
  * ncomponents : expected numer of components of a

optional arguments:

  * newton          : generates a NonlinearForm instead of a BilinearForm that triggers assembly of Newton terms for c(u,u,v)
  * a*to            : position of a argument, set a*to = 2 to trigger assembly of c(u,a,v)
  * ansatz_operator : operator used in the spot u (default: Gradient)
  * test_operator   : operator used in the spot v (default: Identity)
  * factor          : additional factor multiplied in assemblxy (default: 1)
  * regions         : specifies in which regions the operator should assemble, default [0] means all regions
  * name            : name for this operator that is used in print messages
  * AT              : specifies on which entities of the grid the operator is assembled (default: ON_CELLS)
  * store           : stores a matrix of the operator with the latest assembly result
