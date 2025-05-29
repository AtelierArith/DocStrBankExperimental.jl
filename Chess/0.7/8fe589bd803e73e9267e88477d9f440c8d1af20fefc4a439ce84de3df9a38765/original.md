```
isok(c::PieceColor)
```

Tests whether a `PieceColor` value is a valid.

Returns `true` if and only if `c` is either `WHITE` or `BLACK`.

# Examples

```julia-repl
julia> isok(WHITE)
true

julia> isok(BLACK)
true

julia> isok(COLOR_NONE)
false

julia> isok(PieceColor(42))
false
```
