```julia
VariableTargetAdjacency(
    m::SparseArrays.SparseMatrixCSC{Tv<:Integer, Ti<:Integer}
) -> ExtendableGrids.VariableTargetAdjacency{Ti} where Ti<:Integer

```

隣接行列から変数ターゲット隣接を作成する
