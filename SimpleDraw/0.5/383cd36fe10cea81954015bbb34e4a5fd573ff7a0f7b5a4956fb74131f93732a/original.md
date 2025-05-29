```
move_j(shape, j)
```

Return the shape obtained by translating `shape` by `j` pixels along the j-axis (horizontal-axis).

See also [`move_i`](@ref), [`move`](@ref).

# Examples

```julia-repl
julia> move_j(Line(Point(9, 5), Point(24, 28)), 3)
Line{Int64}(Point{Int64}(9, 8), Point{Int64}(24, 31))
```
