```
get_height(x)
```

Return the height of `x` (a shape or an image) along the i-axis (vertical-axis, 1st-axis).

See also [`get_width`](@ref).

# Examples

```julia-repl
julia> get_height(Line(Point(9, 5), Point(24, 28)))
16

julia> get_height(falses(32, 64))
32
```
