```
tochar(p::Piece)
```

ピースを文字に変換します。

# 例

```julia-repl
julia> tochar(PIECE_WN)
'N': ASCII/Unicode U+004e (カテゴリ Lu: 大文字の文字)

julia> tochar(PIECE_BK)
'k': ASCII/Unicode U+006b (カテゴリ Ll: 小文字の文字)

julia> tochar(EMPTY)
'?': ASCII/Unicode U+003f (カテゴリ Po: その他の句読点)
```
