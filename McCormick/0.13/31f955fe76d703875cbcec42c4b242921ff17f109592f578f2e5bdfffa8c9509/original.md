```julia
struct DenseMidInv{S<:VecOrMat{Float64}} <: McCormick.AbstractPreconditionerMC
```

A dense LU preconditioner for implicit McCormick relaxation.
