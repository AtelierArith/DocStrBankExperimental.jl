```
flipgraph_planar(n::Integer; modular=false) :: FlipGraphPlanar
```

凸の `n`-角形の `FlipGraphPlanar` を構築します。

`modular=true` の場合、フリップグラフはそのモジュラー形式に縮小されます。

# 例

```julia-repl
julia> flipgraph_planar(6)
FlipGraphPlanar with 14 vertices and 21 edges
```
