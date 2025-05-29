```
isok(p::Piece)
```

Tests wheter a `Piece` value is valid.

Returns `true` if and only if the color and the type of the piece are valid piece color and piece type values, respectively.

# Examples

```julia-repl
julia> isok(PIECE_WB)
true

julia> isok(PIECE_BQ)
true

julia> isok(EMPTY)
false

julia> isok(Piece(-10))
false
```
