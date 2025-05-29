```julia
mutable struct FuzzyART <: AdaptiveResonance.AbstractFuzzyART
```

# Summary

Gamma-Normalized Fuzzy ART learner struct

For module options, see [`AdaptiveResonance.opts_FuzzyART`](@ref).

# References

1. G. Carpenter, S. Grossberg, and D. Rosen, 'Fuzzy ART: Fast stable learning and categorization of analog patterns by an adaptive resonance system,' Neural Networks, vol. 4, no. 6, pp. 759-771, 1991.

# Fields

  * `opts::AdaptiveResonance.opts_FuzzyART`: FuzzyART options struct.

  * `config::AdaptiveResonance.DataConfig`: Data configuration struct.

  * `threshold::Float64`: Operating module threshold value, a function of the vigilance parameter.

  * `labels::Vector{Int64}`: Incremental list of labels corresponding to each F2 node, self-prescribed or supervised.

  * `T::Vector{Float64}`: Activation values for every weight for a given sample.

  * `M::Vector{Float64}`: Match values for every weight for a given sample.

  * `W::ElasticArrays.ElasticMatrix{Float64, V} where V<:DenseVector{Float64}`: Category weight matrix.

  * `n_instance::Vector{Int64}`: Number of weights associated with each category.

  * `n_categories::Int64`: Number of category weights (F2 nodes).

  * `epoch::Int64`: Current training epoch.

  * `stats::Dict{String, Any}`: Runtime statistics for the module, implemented as a dictionary containing entries at the end of each training iteration. These entries include the best-matching unit index and the activation and match values of the winning node.
