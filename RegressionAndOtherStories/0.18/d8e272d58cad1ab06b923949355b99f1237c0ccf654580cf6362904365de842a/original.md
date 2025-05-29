Directed acyclic graph struct to hold FCI algorithm output

### Mutable struct

```julia
DAG(
* `name::AbstractString` : Name for the DAG object
* `g::Graphs.SimpleGraphs.SimpleDiGraph{Int64}` : CausalInference.DiGraph
* `g_tuple_list::Vector{Tuple{Int, Int}}` : DAG definition as vector of edges, e.g. [(:a, :b), ...]
* `g_dot_str::AbstractString` : DAG dot representation (e.g. used for GraphViz)
* `vars::Vector{Symbol}` : Variables in initial DAG
* `est_g::Graphs.SimpleGraphs.SimpleDiGraph{Int64}` : CausalInference.DiGraph
* `est_g_tuple_list::Vector{Tuple{Int, Int}}` : DAG definition as vector of edges, e.g. [(:a, :b), ...]
* `est_g_dot_str::AbstractString` : DAG dot representation (e.g. used for GraphViz)
* `df::DataFrame` : Variable observations
* `cov::NamedArray` : Covariance matrix as NamedArray
)
```

Part of API, exported.
