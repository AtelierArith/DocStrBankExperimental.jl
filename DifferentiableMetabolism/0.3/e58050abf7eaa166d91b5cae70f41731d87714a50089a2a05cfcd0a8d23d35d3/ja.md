```julia
prune_model(
    model::AbstractFBCModels.CanonicalModel.Model,
    solution_fluxes,
    solution_gene_product_amounts,
    reaction_isozymes,
    solution_isozyme_forward_amounts,
    solution_isozyme_reverse_amounts,
    flux_zero_tol::Float64,
    gene_zero_tol::Float64
) -> Tuple{AbstractFBCModels.CanonicalModel.Model, Dict}

```

`model`から`solution`を使用して反応、代謝物、遺伝子を削除します。さらに、フラックスの方向が変更されたことを考慮して、[`prune_reaction_isozymes`](@ref)を使用して`reaction_isozymes`を調整します。

`flux_zero_tol`、`gene_zero_tol`よりも小さいフラックスと遺伝子産物濃度は削除されます。残りの反応に参加しない代謝物も削除されます。

COBREXAでは、逆変数は常に導出量であるため、すべてを前方指向にすることで、モデル全体の変数はこれらだけになります。
