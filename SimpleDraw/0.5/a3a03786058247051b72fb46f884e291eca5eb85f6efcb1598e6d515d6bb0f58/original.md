```
move(shape, i, j)
```

Return the shape obtained by translating `shape` by `i` pixels along the i-axis (vertical-axis) and `j` pixels along the j-axis (horizontal-axis).

See also [`move_i`](@ref), [`move_j`](@ref).

# Examples

```julia-repl
julia> move(Line(Point(9, 5), Point(24, 28)), 2, 3)
Line{Int64}(Point{Int64}(11, 8), Point{Int64}(26, 31))
```
