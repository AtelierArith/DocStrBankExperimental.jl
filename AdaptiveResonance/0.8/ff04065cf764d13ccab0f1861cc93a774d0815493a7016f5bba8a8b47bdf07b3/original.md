```julia
mutable struct SFAM <: AdaptiveResonance.ARTMAP
```

# Summary

Simple Fuzzy ARTMAP struct.

For module options, see [`AdaptiveResonance.opts_SFAM`](@ref).

# References

1. G. A. Carpenter, S. Grossberg, N. Markuzon, J. H. Reynolds, and D. B. Rosen, “Fuzzy ARTMAP: A Neural Network Architecture for Incremental Supervised Learning of Analog Multidimensional Maps,” IEEE Trans. Neural Networks, vol. 3, no. 5, pp. 698-713, 1992, doi: 10.1109/72.159059.

# Fields

  * `opts::AdaptiveResonance.opts_SFAM`: Simplified Fuzzy ARTMAP options struct.

  * `config::AdaptiveResonance.DataConfig`: Data configuration struct.

  * `W::ElasticArrays.ElasticMatrix{Float64, V} where V<:DenseVector{Float64}`: Category weight matrix.

  * `labels::Vector{Int64}`: Incremental list of labels corresponding to each F2 node, self-prescribed or supervised.

  * `n_categories::Int64`: Number of category weights (F2 nodes).

  * `epoch::Int64`: Current training epoch.

  * `T::Vector{Float64}`: DDVFA activation values.

  * `M::Vector{Float64}`: DDVFA match values.

  * `stats::Dict{String, Any}`: Runtime statistics for the module, implemented as a dictionary containing entries at the end of each training iteration. These entries include the best-matching unit index and the activation and match values of the winning node.
