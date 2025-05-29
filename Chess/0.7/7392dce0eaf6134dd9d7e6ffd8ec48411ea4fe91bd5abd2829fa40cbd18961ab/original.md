```
tochar(p::Piece)
```

Converts a piece to a character.

# Examples

```julia-repl
julia> tochar(PIECE_WN)
'N': ASCII/Unicode U+004e (category Lu: Letter, uppercase)

julia> tochar(PIECE_BK)
'k': ASCII/Unicode U+006b (category Ll: Letter, lowercase)

julia> tochar(EMPTY)
'?': ASCII/Unicode U+003f (category Po: Punctuation, other)
```
