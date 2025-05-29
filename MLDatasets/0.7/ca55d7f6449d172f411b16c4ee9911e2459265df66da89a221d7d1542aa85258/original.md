```
OGBDataset(name; dir=nothing)
```

The collection of datasets from the [Open Graph Benchmark: Datasets for Machine Learning on Graphs](https://arxiv.org/abs/2005.00687) paper.

`name` is the name  of one of the datasets (listed [here](https://ogb.stanford.edu/docs/dataset_overview/)) available for node prediction, edge prediction, or graph prediction tasks.

# Examples

## Node prediction tasks

```julia-repl
julia> data = OGBDataset("ogbn-arxiv")
OGBDataset ogbn-arxiv:
  metadata    =>    Dict{String, Any} with 17 entries
  graphs      =>    1-element Vector{MLDatasets.Graph}
  graph_data  =>    nothing

julia> data[:]
Graph:
  num_nodes   =>    169343
  num_edges   =>    1166243
  edge_index  =>    ("1166243-element Vector{Int64}", "1166243-element Vector{Int64}")
  node_data   =>    (val_mask = "29799-trues BitVector", test_mask = "48603-trues BitVector", year = "169343-element Vector{Int64}", features = "128×169343 Matrix{Float32}", label = "169343-element Vector{Int64}", train_mask = "90941-trues BitVector")
  edge_data   =>    nothing

julia> data.metadata
Dict{String, Any} with 17 entries:
  "download_name"         => "arxiv"
  "num classes"           => 40
  "num tasks"             => 1
  "binary"                => false
  "url"                   => "http://snap.stanford.edu/ogb/data/nodeproppred/arxiv.zip"
  "additional node files" => ["node_year"]
  "is hetero"             => false
  "task level"            => "node"
  ⋮                       => ⋮

julia> data = OGBDataset("ogbn-mag")
OGBDataset ogbn-mag:
  metadata    =>    Dict{String, Any} with 17 entries
  graphs      =>    1-element Vector{MLDatasets.HeteroGraph}
  graph_data  =>    nothing

julia> data[:]
Heterogeneous Graph:
  num_nodes     =>    Dict{String, Int64} with 4 entries
  num_edges     =>    Dict{Tuple{String, String, String}, Int64} with 4 entries
  edge_indices  =>    Dict{Tuple{String, String, String}, Tuple{Vector{Int64}, Vector{Int64}}} with 4 entries
  node_data     =>    (year = "Dict{String, Vector{Float32}} with 1 entry", features = "Dict{String, Matrix{Float32}} with 1 entry", label = "Dict{String, Vector{Int64}} with 1 entry")
  edge_data     =>    (reltype = "Dict{Tuple{String, String, String}, Vector{Float32}} with 4 entries",)
```

## Edge prediction task

```julia-repl
julia> data = OGBDataset("ogbl-collab")
OGBDataset ogbl-collab:
  metadata    =>    Dict{String, Any} with 15 entries
  graphs      =>    1-element Vector{MLDatasets.Graph}
  graph_data  =>    nothing

julia> data[:]
Graph:
  num_nodes   =>    235868
  num_edges   =>    2358104
  edge_index  =>    ("2358104-element Vector{Int64}", "2358104-element Vector{Int64}")
  node_data   =>    (features = "128×235868 Matrix{Float32}",)
  edge_data   =>    (year = "2×1179052 Matrix{Int64}", weight = "2×1179052 Matrix{Int64}")
```

## Graph prediction task

```julia-repl
julia> data = OGBDataset("ogbg-molhiv")
OGBDataset ogbg-molhiv:
  metadata    =>    Dict{String, Any} with 17 entries
  graphs      =>    41127-element Vector{MLDatasets.Graph}
  graph_data  =>    (labels = "41127-element Vector{Int64}", train_mask = "32901-trues BitVector", val_mask = "4113-trues BitVector", test_mask = "4113-trues BitVector")

julia> data[1]
(graphs = Graph(19, 40), labels = 0)
```
