```
graph_to_text(g::AbstractGraph, node_labels::AbstractVector{<:AbstractString}=[]; edge_styles::AbstractDict=Dict())
```

Print out a graph `g` as a table of edges labeled by `node_labels`.

# Arguments

  * `g::AbstractGraph`: a graph to print
  * `node_labels::AbstractVector{<:AbstractString}=[]`: labels for nodes (same order as indices of nodes in `g`)
  * `edge_styles::AbstractDict=Dict()`: dictionary of edge styles (e.g. `Dict((1, 2) => "->", (2, 3) => "<->")`)

# Example

```
g = DiGraph(4)
for (i, j) in [(1, 2), (2, 3), (2, 4)]
    add_edge!(g, i, j)
end
graph_to_text(g)
```
