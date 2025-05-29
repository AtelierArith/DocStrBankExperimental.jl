```julia
assemble!(
    S::MinFEM.PDESystem
) -> Union{Nothing, SparseArrays.UMFPACK.UmfpackLU{Float64, Int64}}

```

システムが以前に使用されていない場合、ディリクレ条件のための乗数を持つシステム行列を設定し、それを因数分解します。
