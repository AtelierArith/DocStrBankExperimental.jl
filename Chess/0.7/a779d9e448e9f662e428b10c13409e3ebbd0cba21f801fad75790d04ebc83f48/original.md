```
rooks(b::Board)
```

The set of squares containing rooks of either color.

# Examples

```julia-repl
julia> b = startboard();

julia> rooks(b) == SquareSet(SQ_A1, SQ_H1, SQ_A8, SQ_H8)
true
```
