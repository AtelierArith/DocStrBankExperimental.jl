```
NodeClickHandler(fun)
```

ノードのための `ClickHandler` を初期化します。関数

```
fun(idx, event, axis)
```

を左クリックイベントで呼び出します。ここで `idx` はノードのインデックスです。

# 例

```
julia> using Makie.Colors
julia> g = wheel_digraph(10)
julia> f, ax, p = graphplot(g, node_size=30, node_color=[colorant"red" for i in 1:nv(g)])
julia> function action(idx, event, axis)
           p.node_color[][idx] = rand(RGB)
           p.node_color[] = p.node_color[]
       end
julia> register_interaction!(ax, :nodeclick, NodeClickHandler(action))
```
