```julia
get_ofms(
    N::Matrix{Float64},
    fixed_fluxes::Vector{Int64},
    flux_values::Vector{Float64}
) -> Any

```

Calculate the optimal flux modes of a pruned optimal solution. Arguments:

  * `N`: the stoichiometric matrix of a pruned model
  * `fixed_fluxes`: the indexes of the fixed fluxes
  * `flux_values`: the optimal values of the fixed fluxes

Output: matrix of the OFMs, each column is a different OFM, rows correspond to the reaction indices of the input `N`.
