```julia
Hmultigrid(fineoperator, coarseoperator, smoother, prolongationbases)
```

H-Multigrid preconditioner for finite element operators

# Arguments:

  * `fineoperator::Operator`:                             finite element operator to precondition
  * `coarseoperator::Union{Operator,Multigrid}`:          coarse grid representation of finite element operator to precondition
  * `smoother::AbstractPreconditioner`:                   error relaxation operator, such as Jacobi
  * `prolongationbases::AbstractArray{<:AbstractBasis}`:  element prolongation bases from coarse to fine grid

# Returns:

  * h-multigrid preconditioner object

# Example:

```jldoctest
# setup
mesh = Mesh2D(1.0, 1.0);
ctofbasis = TensorH1LagrangeHProlongationBasis(2, 1, 2, 2);

# operators
function diffusionweakform(du::Array{Float64}, w::Array{Float64})
    dv = du * w[1]
    return [dv]
end
# -- fine
basis = TensorH1LagrangeMacroBasis(2, 3, 1, 2, 2);
inputs = [
    OperatorField(basis, [EvaluationMode.gradient]),
    OperatorField(basis, [EvaluationMode.quadratureweights]),
];
outputs = [OperatorField(basis, [EvaluationMode.gradient])];
finediffusion = Operator(diffusionweakform, mesh, inputs, outputs);
# -- fine
basis = TensorH1LagrangeBasis(2, 3, 1, 2);
inputs = [
    OperatorField(basis, [EvaluationMode.gradient]),
    OperatorField(basis, [EvaluationMode.quadratureweights]),
];
outputs = [OperatorField(basis, [EvaluationMode.gradient])];
coarsediffusion = Operator(diffusionweakform, mesh, inputs, outputs);

# smoother
jacobi = Jacobi(finediffusion);

# preconditioner
multigrid = HMultigrid(finediffusion, coarsediffusion, jacobi, [ctofbasis]);

# verify
println(multigrid)
println(multigrid.fineoperator)

# output

h-multigrid preconditioner
finite element operator:
2d mesh:
    dx: 1.0
    dy: 1.0

2 inputs:
operator field:
  macro-element tensor product basis:
    numbernodes1d: 3
    numberquadraturepoints1d: 6
    numbercomponents: 1
    numberelements1d: 2
    dimension: 2
  evaluation mode:
    gradient
operator field:
  macro-element tensor product basis:
    numbernodes1d: 3
    numberquadraturepoints1d: 6
    numbercomponents: 1
    numberelements1d: 2
    dimension: 2
  evaluation mode:
    quadratureweights

1 output:
operator field:
  macro-element tensor product basis:
    numbernodes1d: 3
    numberquadraturepoints1d: 6
    numbercomponents: 1
    numberelements1d: 2
    dimension: 2
  evaluation mode:
    gradient
```
