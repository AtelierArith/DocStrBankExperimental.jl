```
NodeDrag(p::GraphPlot)
```

ノードのドラッグアンドドロップを可能にします。`:rectanglezoom` インタラクションの登録を解除してください。

# 例

```
julia> g = wheel_graph(10)
julia> f, ax, p = graphplot(g, node_size = [10 for i in 1:nv(g)])
julia> deregister_interaction!(ax, :rectanglezoom)
julia> register_interaction!(ax, :nodehover, NodeHoverHighlight(p))
julia> register_interaction!(ax, :nodedrag, NodeDrag(p))
```
