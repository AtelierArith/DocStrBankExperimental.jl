```
get_width(x)
```

Return the width of `x` (a shape or an image) along the j-axis (horizontal-axis, 2nd-axis).

See also [`get_height`](@ref).

# Examples

```julia-repl
julia> get_width(Line(Point(9, 5), Point(24, 28)))
24

julia> get_width(falses(32, 64))
64
```
