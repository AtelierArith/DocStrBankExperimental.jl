```
EdgeDrag(p::GraphPlot)
```

エッジのドラッグアンドドロップを許可します。`:rectanglezoom` インタラクションの登録を解除してください。

# 例

```
julia> g = wheel_graph(10)
julia> f, ax, p = graphplot(g, edge_width = [3 for i in 1:ne(g)])
julia> deregister_interaction!(ax, :rectanglezoom)
julia> register_interaction!(ax, :edgehover, EdgeHoverHighlight(p))
julia> register_interaction!(ax, :edgedrag, EdgeDrag(p))
```
