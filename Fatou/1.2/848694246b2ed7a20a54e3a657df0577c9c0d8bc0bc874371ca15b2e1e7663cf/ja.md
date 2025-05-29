```
orbit(K::Fatou.Define)
orbit(u::Function, ∂, orbit, depth, n)
```

主な `Fatou.Define` 関数の関数合成を任意の `depth` までプロットし、`x0` 開始点からの `orbit` 深度を含むコブウェブプロットを作成します。

# 例

```Julia
julia> juliafill("z^2-0.67",∂=[-1.25,1.5],x0=1.25,orbit=17,depth=3) |> orbit
```
