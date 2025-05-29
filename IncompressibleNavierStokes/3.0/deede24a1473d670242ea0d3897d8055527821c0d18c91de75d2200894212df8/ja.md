```julia
pad_vectorfield_mat(
    setup
) -> SparseArrays.SparseMatrixCSC{Tv, Int64} where Tv

```

境界ボリュームで内部ベクトルフィールドをパディングするための行列を作成します。 [`pad_scalarfield_mat`](@ref) に似ています。
