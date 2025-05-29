```
tostring(s::Square)
```

正方形を標準代数表記の文字列に変換します。正方形が無効な値を持つ場合、返される文字列は `"??"` です。

# 例

```julia-repl
julia> tostring(SQ_E4)
"e4"

julia> tostring(Square(100))
"??"
```
