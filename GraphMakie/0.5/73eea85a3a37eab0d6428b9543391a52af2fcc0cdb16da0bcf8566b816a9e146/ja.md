```
NodeHoverHeighlight(p::GraphPlot, factor=2)
```

カーソルの下にあるノードの `node_size` を `factor` 倍に拡大します。

# 例

```
julia> g = wheel_graph(10)
julia> f, ax, p = graphplot(g, node_size = [20 for i in 1:nv(g)])
julia> register_interaction!(ax, :nodehover, NodeHoverHighlight(p))
```
