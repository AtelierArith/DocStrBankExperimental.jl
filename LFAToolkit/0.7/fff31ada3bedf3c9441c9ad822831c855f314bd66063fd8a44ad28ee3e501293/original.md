```julia
Pmultigrid(fineoperator, coarseoperator, smoother, prolongationbases)
```

P-Multigrid preconditioner for finite element operators

# Arguments:

  * `fineoperator::Operator`:                             finite element operator to precondition
  * `coarseoperator::Union{Operator,Multigrid}`:          coarse grid representation of finite element operator to precondition
  * `smoother::AbstractPreconditioner`:                   error relaxation operator, such as Jacobi
  * `prolongationbases::AbstractArray{<:AbstractBasis}`:  element prolongation bases from coarse to fine grid

# Returns:

  * p-multigrid preconditioner object

# Example:

```jldoctest
# setup
mesh = Mesh2D(1.0, 1.0);
ctofbasis = TensorH1LagrangePProlongationBasis(3, 5, 1, 2);

# operators
finediffusion = GalleryOperator("diffusion", 5, 5, mesh);
coarsediffusion = GalleryOperator("diffusion", 3, 5, mesh);

# smoother
jacobi = Jacobi(finediffusion);

# preconditioner
multigrid = PMultigrid(finediffusion, coarsediffusion, jacobi, [ctofbasis]);

# verify
println(multigrid)
println(multigrid.fineoperator)

# output

p-multigrid preconditioner
finite element operator:
2d mesh:
    dx: 1.0
    dy: 1.0

2 inputs:
operator field:
  tensor product basis:
    numbernodes1d: 5
    numberquadraturepoints1d: 5
    numbercomponents: 1
    dimension: 2
  evaluation mode:
    gradient
operator field:
  tensor product basis:
    numbernodes1d: 5
    numberquadraturepoints1d: 5
    numbercomponents: 1
    dimension: 2
  evaluation mode:
    quadratureweights

1 output:
operator field:
  tensor product basis:
    numbernodes1d: 5
    numberquadraturepoints1d: 5
    numbercomponents: 1
    dimension: 2
  evaluation mode:
    gradient
```
