```
piecefromchar(ch::Char)
```

Tries to convert a character to a `Piece`.

The return value is a `Union{Piece, Nothing}`. If the input character is a valid English piece letter, the corresponding piece is returned. If the piece letter is uppercase, the piece is white. If the piece letter is lowercase, the piece is black.

If the input value is not a valid English piece letter, the function returns `nothing`.

# Examples

```julia-repl
julia> piecefromchar('Q')
PIECE_WQ

julia> piecefromchar('n')
PIECE_BN

julia> piecefromchar('-') == nothing
true
```
