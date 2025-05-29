```
get_i_max(shape)
```

Return the maximum index of the bounding box of `shape` along the i-axis (vertical-axis, 1st-axis).

See also [`get_i_min`](@ref), [`get_j_min`](@ref), [`get_j_max`](@ref).

# Examples

```julia-repl
julia> get_i_max(Line(Point(9, 5), Point(24, 28)))
24
```
