```julia
Multigrid(fineoperator, coarseoperator, smoother, prolongation, multigridtype)
```

Multigrid preconditioner for finite element operators

# Arguments:

  * `fineoperator::Operator`:                             finite element operator to precondition
  * `coarseoperator::Union{Operator,Multigrid}`:          coarse grid representation of finite element operator to precondition
  * `smoother::AbstractPreconditioner`:                   error relaxation operator, such as Jacobi
  * `prolongationbases::AbstractArray{<:AbstractBasis}`:  element prolongation bases from coarse to fine grid
  * `multigridtype::MultigridType`:                       multigrid type, h-multigrid or p-multigrid

# Returns:

  * multigrid preconditioner object
