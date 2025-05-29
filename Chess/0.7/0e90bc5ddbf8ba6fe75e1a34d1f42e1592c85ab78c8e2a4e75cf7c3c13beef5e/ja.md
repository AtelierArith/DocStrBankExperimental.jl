```
tochar(c::PieceColor)
```

色を文字に変換します。

# 例

```julia-repl
julia> tochar(WHITE)
'w': ASCII/Unicode U+0077 (category Ll: Letter, lowercase)

julia> tochar(BLACK)
'b': ASCII/Unicode U+0062 (category Ll: Letter, lowercase)

julia> tochar(COLOR_NONE)
'?': ASCII/Unicode U+003f (category Po: Punctuation, other)
```
