```
AggregatedRegDIDResult{TR,Haslsweights,P<:RegressionBasedDIDResult,I} <: AggregatedDIDResult{TR,P}
```

Estimation results aggregated from a [`RegressionBasedDIDResult`](@ref). See also [`agg`](@ref).

# Fields

  * `parent::P`: the [`RegressionBasedDIDResult`](@ref) from which the results are generated.
  * `inds::I`: indices of the coefficient estimates from `parent` used to generate the results.
  * `coef::Vector{Float64}`: coefficient estimates.
  * `vcov::Matrix{Float64}`: variance-covariance matrix for the estimates.
  * `coefweights::Matrix{Float64}`: coefficient weights used to aggregate the coefficient estimates from `parent`.
  * `treatweights::Vector{Float64}`: sum of `treatweights` from `parent` over combined `treatcells`.
  * `treatcounts::Vector{Int}`: sum of `treatcounts` from `parent` over combined `treatcells`.
  * `coefnames::Vector{String}`: coefficient names.
  * `coefinds::Dict{String, Int}`: a map from `coefnames` to integer indices for retrieving estimates by name.
  * `treatcells::VecColumnTable`: cells combined from the `treatcells` from `parent`.
  * `lsweights::Union{TableIndexedMatrix, Nothing}`: cell-level least-square weights.
  * `cellymeans::Union{Vector{Float64}, Nothing}`: cell-level averages of the outcome variable.
  * `cellweights::Union{Vector{Float64}, Nothing}`: total sample weights for each cell.
  * `cellcounts::Union{Vector{Int}, Nothing}`: number of observations for each cell.
