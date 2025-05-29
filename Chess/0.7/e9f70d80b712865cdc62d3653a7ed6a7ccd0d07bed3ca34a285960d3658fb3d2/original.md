```
issingleton(ss::SquareSet)
```

Determine whether `ss` contains exactly one square.

# Examples

```julia-repl
julia> issingleton(SquareSet(SQ_D5))
true

julia> issingleton(SquareSet(SQ_D5, SQ_C5))
false

julia> issingleton(SS_EMPTY)
false
```
