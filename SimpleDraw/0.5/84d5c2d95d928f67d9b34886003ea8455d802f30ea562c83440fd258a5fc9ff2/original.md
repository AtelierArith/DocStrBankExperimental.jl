```
get_position(x)
```

Return a `Point` corresponding to the position of the top-left corner of `x` (a shape or an image).

# Examples

```julia-repl
julia> get_position(Line(Point(9, 5), Point(24, 28)))
Point{Int64}(9, 5)

julia> get_position(falses(32, 64))
Point{Int64}(1, 1)
```
