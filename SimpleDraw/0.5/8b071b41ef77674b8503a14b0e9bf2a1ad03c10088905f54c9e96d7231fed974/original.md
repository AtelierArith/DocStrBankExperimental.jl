```
get_i_extrema(x)
```

Return the minimum and maximum index of `x` (a shape or an image) along the i-axis (vertical-axis, 1st-axis).

See also [`get_j_extrema`](@ref).

# Examples

```julia-repl
julia> get_i_extrema(Line(Point(9, 5), Point(24, 28)))
(9, 24)

julia> get_i_extrema(falses(32, 64))
(1, 32)
```
