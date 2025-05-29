```
is_valid(shape)
```

Return `true` if `shape` is a valid shape that can be drawn and `false` otherwise.

# Examples

```julia-repl
julia> is_valid(Rectangle(Point(9, 5), 16, 24))
true

julia> is_valid(Rectangle(Point(9, 5), -16, 24))
false
```
