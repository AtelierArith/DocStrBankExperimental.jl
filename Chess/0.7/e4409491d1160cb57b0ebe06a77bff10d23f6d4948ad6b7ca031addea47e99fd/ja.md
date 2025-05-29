```
tochar(t::PieceType, uppercase = false)
```

`PieceType` 値を文字に変換します。

有効なピースタイプ値は、その標準的な英語代数表記のピースレターに変換されます。無効なピースタイプ値は `'?'` 文字に変換されます。オプションのパラメータ `uppercase` は、文字が大文字か小文字かを制御します。

# 例

```julia-repl
julia> tochar(PAWN)
'p': ASCII/Unicode U+0070 (category Ll: Letter, lowercase)

julia> tochar(ROOK, true)
'R': ASCII/Unicode U+0052 (category Lu: Letter, uppercase)

julia> tochar(PIECE_TYPE_NONE)
'?': ASCII/Unicode U+003f (category Po: Punctuation, other)
```
