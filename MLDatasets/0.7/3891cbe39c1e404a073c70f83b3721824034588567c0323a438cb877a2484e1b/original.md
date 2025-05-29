```
TUDataset(name; dir=nothing)
```

A variety of graph benchmark datasets, *.e.g.* "QM9", "IMDB-BINARY", "REDDIT-BINARY" or "PROTEINS", collected from the [TU Dortmund University](https://chrsmrrs.github.io/datasets/). Retrieve from the TUDataset collection the dataset `name`, where `name` is any of the datasets available [here](https://chrsmrrs.github.io/datasets/docs/datasets/). 

A `TUDataset` object can be indexed to retrieve a specific graph or a subset of graphs.

See [here](https://chrsmrrs.github.io/datasets/docs/format/) for an in-depth  description of the format. 

# Usage Example

```julia-repl
julia> data = TUDataset("PROTEINS")
dataset TUDataset:
  name        =>    PROTEINS
  metadata    =>    Dict{String, Any} with 1 entry
  graphs      =>    1113-element Vector{MLDatasets.Graph}
  graph_data  =>    (targets = "1113-element Vector{Int64}",)
  num_nodes   =>    43471
  num_edges   =>    162088
  num_graphs  =>    1113

julia> data[1]
(graphs = Graph(42, 162), targets = 1)
```
