```julia
dV(grids) -> Any

```

Calculate the volume of each grid cell

# Examples

```jldoctest
julia> using UltraDark

julia> box_length = 1.0;

julia> resol = 16;

julia> g = Grids(box_length, resol);

julia> dV(g) * resol^3 == box_length^3
true
```
