```
tochar(t::PieceType, uppercase = false)
```

Converts a `PieceType` value to a character.

A valid piece type value is converted to its standard English algebraic notation piece letter. Any invalid piece type value is converted to a `'?'` character. The optional parameter `uppercase` controls whether the character is an upper- or lower-case letter.

# Examples

```julia-repl
julia> tochar(PAWN)
'p': ASCII/Unicode U+0070 (category Ll: Letter, lowercase)

julia> tochar(ROOK, true)
'R': ASCII/Unicode U+0052 (category Lu: Letter, uppercase)

julia> tochar(PIECE_TYPE_NONE)
'?': ASCII/Unicode U+003f (category Po: Punctuation, other)
```
