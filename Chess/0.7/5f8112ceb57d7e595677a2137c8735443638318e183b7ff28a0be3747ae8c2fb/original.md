```
bishoplike(b::Board)
```

The set of squares containing bishoplike pieces of either color.

The bishoplike pieces are the pieces that can move like a bishop, i.e. bishops and queens.

# Examples

```julia-repl
julia> b = startboard();

julia> bishoplike(b) == SquareSet(SQ_C1, SQ_D1, SQ_F1, SQ_C8, SQ_D8, SQ_F8)
true
```
