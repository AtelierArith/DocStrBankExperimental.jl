```
georef(table, geoms)
```

Georeference `table` on vector of geometries `geoms` from [Meshes.jl](https://github.com/JuliaGeometry/Meshes.jl)

## Examples

```julia
julia> georef((a=rand(10), b=rand(10)), rand(Point, 10))
```
