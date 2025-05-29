```julia
plot_band_structure!(M<:Union{Model, BdGModel}, path::Vector{Vector{Float64}},  band_index::Vector{Int64} = collect(1:length(M.Ham.bands[begin])) ; labels::Vector{} = repeat([""], length(path)), closed::Bool=true, nearest::Bool=true) --> Plots.plot()
```

Function to plot band structures of the `Model` along a `path` in the BZ determined by the given critical points. Can take in multiple bands into account ∈ `band_index`. `labels` are the Plot labels of the critical points.
