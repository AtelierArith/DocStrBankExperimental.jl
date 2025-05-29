```
ChickenPox(; normalize= true, num_timesteps_in = 8 , num_timesteps_out = 8, dir = nothing)
```

The ChickenPox dataset contains county-level chickenpox cases in Hungary between 2004 and 2014.

`ChickenPox` is composed of a graph with nodes representing counties and edges representing the neighborhoods, and a metadata dictionary containing the correspondence between the node indices and the county names. 

The node features are the number of weekly chickenpox cases in each county. They are represented as an array of arrays of size `(1, num_nodes, num_timesteps_in)`. The target values are the number of weekly chickenpox cases in each county. They are represented as an array of arrays of size `(1, num_nodes, num_timesteps_out)`. In both cases. two consecutive arrays are shifted by one-time step.

The dataset was taken from the [Pytorch Geometric Temporal repository](https://pytorch-geometric-temporal.readthedocs.io/en/latest/modules/dataset.html#torch_geometric_temporal.dataset.chickenpox.ChickenpoxDatasetLoader) and more information about the dataset can be found in the paper ["Chickenpox Cases in Hungary: a Benchmark Dataset for Spatiotemporal Signal Processing with Graph Neural Networks"](https://arxiv.org/pdf/2102.08100).

# Keyword Arguments

  * `normalize::Bool`: Whether to normalize the data using Z-score normalization. Default is `true`.
  * `num_timesteps_in::Int`: The number of time steps, in this case, the number of weeks, for the input features. Default is `8`.
  * `num_timesteps_out::Int`: The number of time steps, in this case, the number of weeks, for the target values. Default is `8`.
  * `dir::String`: The directory to save the dataset. Default is `nothing`.

# Examples

```julia-repl
julia> using JSON3 # import JSON3

julia> dataset = ChickenPox()
dataset ChickenPox:
  metadata  =>    Dict{Symbol, Any} with 20 entries
  graphs    =>    1-element Vector{MLDatasets.Graph}

julia> dataset.graphs[1].num_nodes # 20 counties
20

julia> size(dataset.graphs[1].node_data.features[1]) 
(1, 20, 8)

julia> dataset.metadata[:BUDAPEST] # The node 5 correponds to Budapest county 
5
```
