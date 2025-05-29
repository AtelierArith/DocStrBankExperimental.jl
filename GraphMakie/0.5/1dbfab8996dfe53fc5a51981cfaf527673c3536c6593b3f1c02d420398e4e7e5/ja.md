```
EdgeHoverHeighlight(p::GraphPlot, factor=2)
```

カーソルの下にあるエッジの `edge_width` を `factor` 倍に拡大します。もし `arrow_size` が `Vector{<:Real}` の場合、矢印の散布も拡大します。

# 例

```
julia> g = wheel_digraph(10)
julia> f, ax, p = graphplot(g, edge_width = [3 for i in 1:ne(g)],
                               arrow_size=[10 for i in 1:ne(g)])
julia> register_interaction!(ax, :nodehover, EdgeHoverHighlight(p))
```
