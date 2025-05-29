```julia
assemble!(
    S::MinFEM.PDESystem
) -> Union{Nothing, SparseArrays.UMFPACK.UmfpackLU{Float64, Int64}}

```

If the system has not been used before, sets up the system matrix  with multipliers for Dirichlet conditions and factorizes it.
