```
EdgeClickHandler(fun)
```

エッジのための `ClickHandler` を初期化します。左クリックイベントで関数

```
fun(idx, event, axis)
```

を呼び出します。ここで `idx` はエッジインデックスです。

# 例

```
julia> using Makie.Colors
julia> g = wheel_digraph(10)
julia> f, ax, p = graphplot(g, edge_width=4, edge_color=[colorant"black" for i in 1:ne(g)])
julia> function action(idx, event, axis)
           p.edge_color[][idx] = rand(RGB)
           p.edge_color[] = p.edge_color[]
       end
julia> register_interaction!(ax, :edgeclick, EdgeClickHandler(action))
```
