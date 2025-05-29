```
tostring(s::Square)
```

Converts a square to a string in standard algebraic notation. If the square has an invalid value, the returned string is `"??"`.

# Examples

```julia-repl
julia> tostring(SQ_E4)
"e4"

julia> tostring(Square(100))
"??"
```
