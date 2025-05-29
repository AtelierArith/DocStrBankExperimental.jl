```
AQSOL(; split=:train, dir=nothing)
```

The AQSOL (Aqueous Solubility) dataset from the paper  [Graph Neural Network for Predicting Aqueous Solubility of Organic Molecules](http://arxiv.org/abs/2003.00982).

The dataset contains 9,882 graphs representing small organic molecules. Each graph represents a molecule, where nodes correspond to atoms and edges to bonds. The node features represent the atomic number, and the edge features represent the bond type. The target is the aqueous solubility of the molecule, measured in mol/L.

# Arguments

  * `split`: Which split of the dataset to load. Can be one of `:train`, `:val`, or `:test`. Defaults to `:train`.
  * `dir`: Directory in which the dataset is in.

# Examples

```julia-repl
julia> using MLDatasets

julia> data = AQSOL()
dataset AQSOL:
  split     =>    :train
  metadata  =>    Dict{String, Any} with 1 entry
  graphs    =>    7985-element Vector{MLDatasets.Graph}

julia> length(data)
7985

julia> g = data[1]
Graph:
  num_nodes   =>    23
  num_edges   =>    42
  edge_index  =>    ("42-element Vector{Int64}", "42-element Vector{Int64}")
  node_data   =>    (features = "23-element Vector{Int64}",)
  edge_data   =>    (features = "42-element Vector{Int64}",)

julia> g.num_nodes
23

julia> g.node_data.features
23-element Vector{Int64}:
 0
 1
 1
 ⋮
 1
 1
 1

julia> g.edge_index
([2, 3, 3, 4, 4, 5, 5, 6, 6, 7  …  18, 19, 19, 20, 20, 21, 20, 22, 20, 23], [3, 2, 4, 3, 5, 4, 6, 5, 7, 6  …  19, 18, 20, 19, 21, 20, 22, 20, 23, 20])
```
