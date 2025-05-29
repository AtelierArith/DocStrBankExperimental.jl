```
georef(table, domain)
```

`table`を[Meshes.jl](https://github.com/JuliaGeometry/Meshes.jl)の`domain`にジオリファレンスします。

## 例

```julia
julia> georef((a=rand(100), b=rand(100)), CartesianGrid(10, 10))
```
