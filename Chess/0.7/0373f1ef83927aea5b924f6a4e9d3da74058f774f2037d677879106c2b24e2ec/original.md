```
knights(b::Board)
```

The set of squares containing knights of either color.

# Examples

```julia-repl
julia> b = startboard();

julia> knights(b) == SquareSet(SQ_B1, SQ_G1, SQ_B8, SQ_G8)
true
```
