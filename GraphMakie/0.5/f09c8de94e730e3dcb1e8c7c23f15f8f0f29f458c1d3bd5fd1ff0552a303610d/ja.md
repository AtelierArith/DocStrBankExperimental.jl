```
NodeDragHandler(fun)
```

ノードのための `DragHandler` を初期化します。関数

```
fun(dragstate, idx, event, axis)
```

が呼び出され、`dragstate=true` はドラッグ中、`false` はドラッグの最後の時点で `fun` がトリガーされるときです。`idx` はノードのインデックスです。

# 例

```
julia> g = wheel_digraph(10)
julia> f, ax, p = graphplot(g, node_size=20)
julia> deregister_interaction!(ax, :rectanglezoom)
julia> function action(state, idx, event, axis)
           p[:node_pos][][idx] = event.data
           p[:node_pos][] = p[:node_pos][]
       end
julia> register_interaction!(ax, :nodedrag, NodeDragHandler(action))
```
