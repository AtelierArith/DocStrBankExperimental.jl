```
squaresbetween(s1::Square, s2::Square)
```

The set of squares on the line, file or diagonal between `s1` and `s2`.

When a queen on `s1` would attack `s2` on an otherwise empty board, this function returns the set of squares where a piece would block the queen on `s1` from attacking `s2`.

# Examples

```julia-repl
julia> squaresbetween(SQ_A4, SQ_D4) == SquareSet(SQ_B4, SQ_C4)
true

julia> squaresbetween(SQ_F7, SQ_A2)
SquareSet:
 -  -  -  -  -  -  -  -
 -  -  -  -  -  -  -  -
 -  -  -  -  #  -  -  -
 -  -  -  #  -  -  -  -
 -  -  #  -  -  -  -  -
 -  #  -  -  -  -  -  -
 -  -  -  -  -  -  -  -
 -  -  -  -  -  -  -  -
```
