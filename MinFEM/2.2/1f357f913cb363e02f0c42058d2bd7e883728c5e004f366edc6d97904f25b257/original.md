```julia
solve!(S::MinFEM.PDESystem) -> Any

```

First tries to [assemble!](@ref) the system matrix with multipliers for Dirichlet conditions. If the system has already been used before, this step is skipped. This is determined depending on an existing factorization of the system matrix. If the stiffness matrix or Dirichlet conditions have changes,  one should invole [refresh!](@ref) first. Finally the system is solved via matrix factorization.
