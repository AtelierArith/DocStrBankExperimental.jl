```
vLine(
    height::Int;
    style::String = TERM_THEME[].line,
    box::Symbol = TERM_THEME[].box,
    char::Union{Char,Nothing} = nothing,
)
```

高さを指定して、オプションでスタイル情報を指定して `vLine` を作成します。
