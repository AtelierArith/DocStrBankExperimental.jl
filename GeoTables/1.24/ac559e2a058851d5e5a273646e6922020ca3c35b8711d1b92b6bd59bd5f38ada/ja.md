```
georef(table, geoms)
```

`table`を[Meshes.jl](https://github.com/JuliaGeometry/Meshes.jl)の幾何学のベクトル`geoms`にジオリファレンスします。

## 例

```julia
julia> georef((a=rand(10), b=rand(10)), rand(Point, 10))
```
