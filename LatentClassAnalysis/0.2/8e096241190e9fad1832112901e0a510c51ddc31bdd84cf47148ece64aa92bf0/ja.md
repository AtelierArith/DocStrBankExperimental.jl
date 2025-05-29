```
show_profiles(model::LCAModel, data::DataFrame, cols::Vector{Symbol}; 
             var_names::Union{Nothing, Vector{String}}=nothing,
             var_labels::Union{Nothing, Vector{Vector{String}}}=nothing,
             digits::Int=3)
```

潜在クラスプロファイルを整列した列で表示します。
