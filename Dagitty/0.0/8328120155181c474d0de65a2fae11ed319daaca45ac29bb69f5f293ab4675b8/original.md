```
DAG
```

Structure with fields:

  * `graph::SimpleDiGraph` - underlying directed graph
  * `labels::Vector{Symbol}` - vector of each nodes' label

Could be constructed by passing list of `Pair{Symbol, Symbol}`

# Examples

```jldoctest
julia> using Dagitty

julia> g = DAG(:A => :B)
DAG: {2, 1} directed simple Int64 graph with labels [:A, :B])

julia> g.graph
{2, 1} directed simple Int64 graph

julia> g.labels
2-element Vector{Symbol}:
 :A
 :B

julia> g = DAG(:A => :A)
ERROR: DAGHasLoops()
```
