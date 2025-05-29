```julia
differentiate_prepare_kkt(
    m::ConstraintTrees.ConstraintTree,
    objective::ConstraintTrees.Value,
    parameters::Vector{Symbol}
) -> Tuple{Tuple{SparseArrays.SparseMatrixCSC{FastDifferentiation.Node, Int64}, SparseArrays.SparseMatrixCSC{FastDifferentiation.Node, Int64}, Vector{FastDifferentiation.Node}, Vector{FastDifferentiation.Node}, Vector{FastDifferentiation.Node}, Vector{Symbol}}, Any}

```

Prepare a model `m` with `objective` for differentiation with respect to `parameters`.

This is the most time consuming aspect of differentiation. It pays off to do this separately  if the same model will be differentiated multiple times.
