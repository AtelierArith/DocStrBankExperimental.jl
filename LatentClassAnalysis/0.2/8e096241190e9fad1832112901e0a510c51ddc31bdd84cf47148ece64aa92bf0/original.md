```
show_profiles(model::LCAModel, data::DataFrame, cols::Vector{Symbol}; 
             var_names::Union{Nothing, Vector{String}}=nothing,
             var_labels::Union{Nothing, Vector{Vector{String}}}=nothing,
             digits::Int=3)
```

Display the latent class profiles with aligned columns.
