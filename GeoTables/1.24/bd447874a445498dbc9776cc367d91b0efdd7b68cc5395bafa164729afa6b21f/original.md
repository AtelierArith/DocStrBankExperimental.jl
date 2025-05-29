```
georef(table, domain)
```

Georeference `table` on `domain` from [Meshes.jl](https://github.com/JuliaGeometry/Meshes.jl)

## Examples

```julia
julia> georef((a=rand(100), b=rand(100)), CartesianGrid(10, 10))
```
