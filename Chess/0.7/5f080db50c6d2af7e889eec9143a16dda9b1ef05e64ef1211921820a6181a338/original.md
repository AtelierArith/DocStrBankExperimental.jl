```
kings(b::Board)
```

The set of squares containing kings of either color.

# Examples

```julia-repl
julia> b = startboard();

julia> kings(b) == SquareSet(SQ_E1, SQ_E8)
true
```
