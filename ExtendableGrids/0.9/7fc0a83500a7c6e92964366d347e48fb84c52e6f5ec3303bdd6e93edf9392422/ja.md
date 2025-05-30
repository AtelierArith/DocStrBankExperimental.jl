```julia
VariableTargetAdjacency(
    m::SparseArrays.SparseMatrixCSC{Tv<:Integer, Ti<:Integer}
) -> ExtendableGrids.VariableTargetAdjacency{Ti} where Ti<:Integer

```

隣接行列から可変ターゲット隣接行列を作成します。
