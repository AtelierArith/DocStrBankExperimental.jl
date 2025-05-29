```
EdgeHoverHeighlight(p::GraphPlot, factor=2)
```

Magnifies the `edge_width` of edge under cursor by `factor`. If `arrow_size isa Vector{<:Real}` it also magnifies the arrow scatter.

# Example

```
julia> g = wheel_digraph(10)
julia> f, ax, p = graphplot(g, edge_width = [3 for i in 1:ne(g)],
                               arrow_size=[10 for i in 1:ne(g)])
julia> register_interaction!(ax, :nodehover, EdgeHoverHighlight(p))
```
