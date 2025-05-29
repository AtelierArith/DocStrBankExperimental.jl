```julia
mutable struct DDVFA <: AdaptiveResonance.ART
```

# Summary

Distributed Dual Vigilance Fuzzy ARTMAP module struct.

For module options, see [`AdaptiveResonance.opts_DDVFA`](@ref).

# References

1. L. E. Brito da Silva, I. Elnabarawy, and D. C. Wunsch, 'Distributed dual vigilance fuzzy adaptive resonance theory learns online, retrieves arbitrarily-shaped clusters, and mitigates order dependence,' Neural Networks, vol. 121, pp. 208-228, 2020, doi: 10.1016/j.neunet.2019.08.033.
2. G. Carpenter, S. Grossberg, and D. Rosen, 'Fuzzy ART: Fast stable learning and categorization of analog patterns by an adaptive resonance system,' Neural Networks, vol. 4, no. 6, pp. 759-771, 1991.

# Fields

  * `opts::AdaptiveResonance.opts_DDVFA`: DDVFA options struct.

  * `subopts::AdaptiveResonance.opts_FuzzyART`: FuzzyART options struct used for all F2 nodes.

  * `config::AdaptiveResonance.DataConfig`: Data configuration struct.

  * `threshold::Float64`: Operating module threshold value, a function of the vigilance parameter.

  * `F2::Vector{AdaptiveResonance.FuzzyART}`: List of F2 nodes (themselves FuzzyART modules).

  * `labels::Vector{Int64}`: Incremental list of labels corresponding to each F2 node, self-prescribed or supervised.

  * `n_categories::Int64`: Number of total categories.

  * `epoch::Int64`: Current training epoch.

  * `T::Vector{Float64}`: DDVFA activation values.

  * `M::Vector{Float64}`: DDVFA match values.

  * `stats::Dict{String, Any}`: Runtime statistics for the module, implemented as a dictionary containing entries at the end of each training iteration. These entries include the best-matching unit index and the activation and match values of the winning node.
