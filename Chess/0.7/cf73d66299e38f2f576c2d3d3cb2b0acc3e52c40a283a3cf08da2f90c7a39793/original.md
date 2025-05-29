```
queens(b::Board)
```

The set of squares containing queens of either color.

# Examples

```julia-repl
julia> b = startboard();

julia> queens(b) == SquareSet(SQ_D1, SQ_D8)
true
```
