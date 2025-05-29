```
netgraphplot(ng::NetsedGraph)
netgraphplot!(ax, ng::NetsedGraph)
```

Creates a graph plot of the ng represented as a `NestedGraph`.

## Attributes

  * `show_routers = false`: show labels for nodes
  * `show_links = false`: show labels for links.
  * `color_paths = nothing`: color given paths.

You must pass in `Vector{Vector{Integer}}` where each nested `Vector` is a path. Each path is being colored with a distinct color.

  * `color_edges = nothing`: color given edges.

Pass in `Vector{Vector{Edge}}`.  Each nested Vector{Edge} gets a distinct color.

  * `pure_colors = nothing`: enter a `Vector` of colors to use for edges/paths.
  * `circle_nodes = nothing`: choose which nodes to circle.

Pass in Vector{Vector{Int}}. Each nested Vector{Int} gets the same color.
