```
colorfromchar(c::Char)
```

Tries to convert a character to a `PieceColor`.

The return value is a `Union{PieceColor, Nothing}`. If the input character is one of the four characters `'w'`, `'b'`, `'W'`, `'B'`, the function returns the obvious corresponding color (`WHITE` or `BLACK`). For all other input characters, the function returns `nothing`.

# Examples

```julia-repl
julia> colorfromchar('w') == WHITE
true

julia> colorfromchar('B') == BLACK
true

julia> colorfromchar('x') == nothing
true
```
