```
EdgeDrag(p::GraphPlot)
```

Allows drag and drop of Edges. Please deregister the `:rectanglezoom` interaction.

# Example

```
julia> g = wheel_graph(10)
julia> f, ax, p = graphplot(g, edge_width = [3 for i in 1:ne(g)])
julia> deregister_interaction!(ax, :rectanglezoom)
julia> register_interaction!(ax, :edgehover, EdgeHoverHighlight(p))
julia> register_interaction!(ax, :edgedrag, EdgeDrag(p))
```
