```
NodeHoverHandler(fun)
```

ノードのための `HoverHandler` を初期化します。関数

```
fun(hoverstate, idx, event, axis)
```

をホバー時に `hoverstate=true` で、ホバー終了時に `false` で呼び出します。`idx` はノードのインデックスです。

# 例

```
julia> g = wheel_digraph(10)
julia> f, ax, p = graphplot(g, node_size = [20 for i in 1:nv(g)])
julia> function action(state, idx, event, axis)
           p.node_size[][idx] = state ? 40 : 20
           p.node_size[] = p.node_size[] #observableをトリガー
       end
julia> register_interaction!(ax, :nodehover, NodeHoverHandler(action))
```
