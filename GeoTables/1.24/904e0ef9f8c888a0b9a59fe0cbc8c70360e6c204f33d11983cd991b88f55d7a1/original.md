```
georef(tuple)
```

Georeference a named `tuple` on `CartesianGrid(dims)`, with `dims` obtained from the arrays stored in the tuple.

## Examples

```julia
julia> georef((a=rand(10, 10), b=rand(10, 10))) # 2D grid
julia> georef((a=rand(10, 10, 10), b=rand(10, 10, 10))) # 3D grid
```
