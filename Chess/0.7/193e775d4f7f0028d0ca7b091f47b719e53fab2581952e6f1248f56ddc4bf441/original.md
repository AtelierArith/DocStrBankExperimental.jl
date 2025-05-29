```
onlyfirst(ss::SquareSet)
```

Return a square set with all squares except the first removed.

# Examples

```julia-repl
julia> onlyfirst(SquareSet(SQ_A4, SQ_D5, SQ_F6)) == SquareSet(SQ_A4)
true
```
