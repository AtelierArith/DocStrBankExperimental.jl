```
isok(r::SquareRank)
```

Tests whether a `SquareRank` contains a valid value.

# Examples

```julia-repl
julia> isok(RANK_6)
true

julia> isok(SquareRank(42))
false
```
