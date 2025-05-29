```
WindMillEnergy(; size, normalize=true, num_timesteps_in=8, num_timesteps_out=8, dir=nothing)
```

The WindMillEnergy dataset contains a collection hourly energy output of windmills from a European country for more than 2 years. 

`WindMillEnergy` is a graph with nodes representing windmills. The edge weights represent the strength of the relationship between the windmills. The number of nodes is fixed and depends on the size of the dataset, 11 for `small`, 26 for `medium`, and 319 for `large`.

The node features and targets are the number of hourly energy output of the windmills. They are represented as an array of arrays of size `(1, num_nodes, num_timesteps_in)`. In both cases, two consecutive arrays are shifted by one-time step.

# Keyword Arguments

  * `size::String`: The size of the dataset, can be `small`, `medium`, or `large`.
  * `normalize::Bool`: Whether to normalize the data using Z-score normalization. Default is `true`.
  * `num_timesteps_in::Int`: The number of time steps, in this case, the number of hours, for the input features. Default is `8`.
  * `num_timesteps_out::Int`: The number of time steps, in this case, the number of hours, for the target values. Default is `8`.
  * `dir::String`: The directory to save the dataset. Default is `nothing`.

# Examples

```julia-repl
julia> using JSON3

julia> dataset = WindMillEnergy(;size= "small");

julia> dataset.graphs[1]
Graph:
  num_nodes   =>    11
  num_edges   =>    121
  edge_index  =>    ("121-element Vector{Int64}", "121-element Vector{Int64}")
  node_data   =>    (features = "17456-element Vector{Any}", targets = "17456-element Vector{Any}")
  edge_data   =>    121-element Vector{Float32}

julia> size(dataset.graphs[1].node_data.features[1])
(1, 11, 8)
```
