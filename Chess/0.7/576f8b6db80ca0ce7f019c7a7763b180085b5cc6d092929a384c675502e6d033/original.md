```
piecetypefromchar(c::Chars)
```

Tries to convert a character to a `PieceType`.

The return value is a `Union{PieceType, Nothing}`. If the input character is a valid upper- or lowercase English piece letter (PNBRQK), the function returns the corresponding piece type. For all other input characters, the function returns `nothing`.

# Examples

```julia-repl
julia> piecetypefromchar('n') == KNIGHT
true

julia> piecetypefromchar('B') == BISHOP
true

julia> piecetypefromchar('a') == nothing
true
```
