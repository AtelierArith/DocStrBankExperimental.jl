```
filesquares(f::SquareFile)
filesquares(s::Square)
```

提供されたファイル上のすべての正方形の集合。

# 例

```julia-repl
julia> filesquares(FILE_G) == SS_FILE_G
true

julia> filesquares(SQ_C5) == SS_FILE_C
true
```
