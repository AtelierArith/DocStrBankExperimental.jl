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

Prune away reactions, metabolites, and genes from a `model` using `solution`. Additionally, adjust `reaction_isozymes` using [`prune_reaction_isozymes`](@ref) to account for the changed directions of the fluxes.

Fluxes and gene product concentrations smaller than `flux_zero_tol`, `gene_zero_tol` are removed. Metabolites that do not take part in the remaining reactions are also removed.

Note, in COBREXA reverse variables are always derived quantities, hence making everything forward orientated ensures that the variables of the whole model are just these.
