```julia
differentiate_prepare_kkt(
    m::ConstraintTrees.ConstraintTree,
    objective::ConstraintTrees.Value,
    parameters::Vector{Symbol}
) -> Tuple{Tuple{SparseArrays.SparseMatrixCSC{FastDifferentiation.Node, Int64}, SparseArrays.SparseMatrixCSC{FastDifferentiation.Node, Int64}, Vector{FastDifferentiation.Node}, Vector{FastDifferentiation.Node}, Vector{FastDifferentiation.Node}, Vector{Symbol}}, Any}

```

モデル `m` を `objective` とともに、`parameters` に関して微分のために準備します。

これは微分の中で最も時間がかかる側面です。同じモデルを複数回微分する場合は、これを別々に行う価値があります。
