```
isok(t::PieceType)
```

Tests whether a `PieceType` value is valid.

Returns `true` for all of `PAWN`, `KNIGHT`, `BISHOP`, `ROOK`, `QUEEN` and `KING`, and `false` for all other inputs.

# Examples

```julia-repl
julia> isok(QUEEN)
true

julia> isok(KNIGHT)
true

julia> isok(PIECE_TYPE_NONE)
false

julia> isok(PieceType(-1))
false
```
