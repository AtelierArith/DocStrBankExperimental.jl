```
get_j_max(shape)
```

Return the maximum index of the bounding box of `shape` along the j-axis (horizontal-axis, 2nd-axis).

See also [`get_j_min`](@ref), [`get_i_min`](@ref), [`get_i_max`](@ref).

# Examples

```julia-repl
julia> get_j_max(Line(Point(9, 5), Point(24, 28)))
28
```
