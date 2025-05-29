```julia
refresh!(
    S::MinFEM.PDESystem
) -> Union{Nothing, SparseArrays.UMFPACK.UmfpackLU{Float64, Int64}}

```

Recomputes the factorization of the stiffness matrix using [assemble!](@ref).
