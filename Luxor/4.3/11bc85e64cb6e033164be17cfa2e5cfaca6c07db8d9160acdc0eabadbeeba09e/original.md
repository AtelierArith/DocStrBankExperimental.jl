```
rescale(x, from_min, from_max, to_min=0.0, to_max=1.0)
```

Convert `x` from one linear scale (`from_min` to `from_max`) to another (`to_min` to `to_max`).

The scales can also be supplied in tuple form:

```julia
rescale(x, (from_min, from_max), (to_min, to_max))
```

Examples

```julia
julia> rescale(15, 0, 100, 0, 1)
0.15

julia> rescale(15, (0, 100), (0, 1))
0.15

julia> rescale(pi/20, 0, 2pi, 0, 1)
0.025

julia> rescale(pi/20, (0, 2pi), (0, 1))
0.025

julia> rescale(25, 0, 1, 0, 1.609344)
40.2336

julia> rescale(15, (0, 100), (1000, 0))
850.0
```
