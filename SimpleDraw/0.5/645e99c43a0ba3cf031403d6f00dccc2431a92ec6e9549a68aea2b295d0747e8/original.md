```
get_i_min(shape)
```

Return the minimum index of the bounding box of `shape` along the i-axis (vertical-axis, 1st-axis).

See also [`get_i_max`](@ref), [`get_j_min`](@ref), [`get_j_max`](@ref).

# Examples

```julia-repl
julia> get_i_min(Line(Point(9, 5), Point(24, 28)))
9
```
