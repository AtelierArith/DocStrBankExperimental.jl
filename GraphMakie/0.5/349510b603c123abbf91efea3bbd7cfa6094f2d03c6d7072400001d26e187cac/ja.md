```
EdgeHoverHandler(fun)
```

エッジのための `HoverHandler` を初期化します。関数

```
fun(hoverstate, idx, event, axis)
```

をホバー時に `hoverstate=true` で、ホバー終了時に `false` で呼び出します。`idx` はエッジのインデックスです。

# 例

```
julia> g = wheel_digraph(10)
julia> f, ax, p = graphplot(g, edge_width = [3.0 for i in 1:ne(g)])
julia> function action(state, idx, event, axis)
           p.edge_width[][idx] = state ? 6.0 : 3.0
           p.edge_width[] = p.edge_width[] #trigger observable
       end
julia> register_interaction!(ax, :edgehover, EdgeHoverHandler(action))
```
