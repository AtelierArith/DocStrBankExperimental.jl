```
removefirst(ss::SquareSet)
```

Remove the first member of a square set.

# Examples

```julia-repl
julia> removefirst(SquareSet(SQ_A4, SQ_D5, SQ_F6)) == SquareSet(SQ_D5, SQ_F6)
true
```
