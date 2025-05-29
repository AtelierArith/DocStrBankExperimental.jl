```
struct DerSPMF{T<:AbstractMatrix,FDtype,TT<:Number} <: AbstractSPMF{T}
```

A DerSPMF is a representation of a NEP defined by a Sum of Products of Matrices and Functions [`SPMF_NEP`](@ref). This format makes the execution of [`compute_Mlincomb`](@ref) for the specified `σ` more efficient.
