```julia
refresh!(
    S::MinFEM.PDESystem
) -> Union{Nothing, SparseArrays.UMFPACK.UmfpackLU{Float64, Int64}}

```

剛性行列の因子分解を[assemble!](@ref)を使用して再計算します。
