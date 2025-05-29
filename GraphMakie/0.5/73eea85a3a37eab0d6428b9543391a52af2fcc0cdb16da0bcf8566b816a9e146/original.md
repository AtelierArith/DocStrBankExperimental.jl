```
NodeHoverHeighlight(p::GraphPlot, factor=2)
```

Magnifies the `node_size` of node under cursor by `factor`.

# Example

```
julia> g = wheel_graph(10)
julia> f, ax, p = graphplot(g, node_size = [20 for i in 1:nv(g)])
julia> register_interaction!(ax, :nodehover, NodeHoverHighlight(p))
```
