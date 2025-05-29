```
move_i(shape, i)
```

Return the shape obtained by translating `shape` by `i` pixels along the i-axis (vertical-axis).

See also [`move_j`](@ref), [`move`](@ref).

# Examples

```julia-repl
julia> move_i(Line(Point(9, 5), Point(24, 28)), 2)
Line{Int64}(Point{Int64}(11, 5), Point{Int64}(26, 28))
```
