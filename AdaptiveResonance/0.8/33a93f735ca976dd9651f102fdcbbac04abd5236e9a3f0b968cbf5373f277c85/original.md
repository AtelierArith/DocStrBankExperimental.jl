```julia
mutable struct DVFA <: AdaptiveResonance.AbstractFuzzyART
```

# Summary

Dual Vigilance Fuzzy ARTMAP module struct.

For module options, see [`AdaptiveResonance.opts_DVFA`](@ref).

# References:

1. L. E. Brito da Silva, I. Elnabarawy and D. C. Wunsch II, 'Dual Vigilance Fuzzy ART,' Neural Networks Letters. To appear.
2. G. Carpenter, S. Grossberg, and D. Rosen, 'Fuzzy ART: Fast stable learning and categorization of analog patterns by an adaptive resonance system,' Neural Networks, vol. 4, no. 6, pp. 759-771, 1991.

# Fields

  * `opts::AdaptiveResonance.opts_DVFA`: DVFA options struct.

  * `config::AdaptiveResonance.DataConfig`: Data configuration struct.

  * `threshold_ub::Float64`: Operating upper bound module threshold value, a function of the upper bound vigilance parameter.

  * `threshold_lb::Float64`: Operating lower bound module threshold value, a function of the lower bound vigilance parameter.

  * `labels::Vector{Int64}`: Incremental list of labels corresponding to each F2 node, self-prescribed or supervised.

  * `W::ElasticArrays.ElasticMatrix{Float64, V} where V<:DenseVector{Float64}`: Category weight matrix.

  * `T::Vector{Float64}`: Activation values for every weight for a given sample.

  * `M::Vector{Float64}`: Match values for every weight for a given sample.

  * `n_categories::Int64`: Number of category weights (F2 nodes).

  * `n_clusters::Int64`: Number of labeled clusters, may be lower than `n_categories`

  * `epoch::Int64`: Current training epoch.

  * `stats::Dict{String, Any}`: Runtime statistics for the module, implemented as a dictionary containing entries at the end of each training iteration. These entries include the best-matching unit index and the activation and match values of the winning node.
