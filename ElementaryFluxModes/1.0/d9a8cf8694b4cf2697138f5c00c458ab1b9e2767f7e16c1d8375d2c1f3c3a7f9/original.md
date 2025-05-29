```julia
differentiate_efm(
    EFMs::Vector{Dict{String, Float64}},
    parameters::Vector{FastDifferentiation.Node},
    rid_pid::Dict{String, FastDifferentiation.Node},
    parameter_values::Dict{Symbol, Float64},
    rid_gcounts::Dict{String, Dict{String, Float64}},
    capacity::Vector{Tuple{String, Vector{String}, Float64}},
    gene_product_molar_masses::Dict{String, Float64},
    optimizer
) -> Any

```

Differentiate the usage of EFMs with respect to changes in the model parameters using implicit differentiation of the Lagrangian. Calculating the proportion of each EFM used in the optimal solution can be turned into the following LP:     maximise     ∑xᵢ     subject to   Dx = 1 where D is the cost matrix associated to each EFM in each enzyme pool. We then differentiate Lagrangian of this LP to calculate the differential of x by parameters.

Arguments:

  * 'EFMs': a vector of dictionaries of EFMs
  * 'parameters': vector of the model parameters
  * `rid_pid`: dict of reaction ids => parameter ids
  * `parameter_values`: dict of parameter symbol => float value
  * `rid_gcounts`: dict of reaction id => gene product counts
  * `capacity`: enzyme capacity limit of the enzyme constrained model
  * `gene_product_molar_masses`: dict of gene product gene*product*molar_masses

Output: Matrix Aᵢⱼ of the the differential of EFM i with respect to parameter j: d(EFMᵢ)/d(pⱼ)
