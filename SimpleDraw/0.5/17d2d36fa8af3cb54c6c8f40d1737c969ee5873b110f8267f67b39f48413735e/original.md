```
get_j_extrema(x)
```

Return the minimum and maximum index of `x` (a shape or an image) along the j-axis (horizontal-axis, 2nd-axis).

See also [`get_i_extrema`](@ref).

# Examples

```julia-repl
julia> get_j_extrema(Line(Point(9, 5), Point(24, 28)))
(5, 28)

julia> get_j_extrema(falses(32, 64))
(1, 64)
```
