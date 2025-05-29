```
adjacentfilesquares(f::SquareFile)
adjacentfilesquares(s::Square)
```

入力ファイルに隣接するファイル上のすべてのスクエアのセット。

# 例

```julia-repl
julia> adjacentfilesquares(FILE_F)
SquareSet:
 -  -  -  -  #  -  #  -
 -  -  -  -  #  -  #  -
 -  -  -  -  #  -  #  -
 -  -  -  -  #  -  #  -
 -  -  -  -  #  -  #  -
 -  -  -  -  #  -  #  -
 -  -  -  -  #  -  #  -
 -  -  -  -  #  -  #  -

julia> adjacentfilesquares(FILE_A)
SquareSet:
 -  #  -  -  -  -  -  -
 -  #  -  -  -  -  -  -
 -  #  -  -  -  -  -  -
 -  #  -  -  -  -  -  -
 -  #  -  -  -  -  -  -
 -  #  -  -  -  -  -  -
 -  #  -  -  -  -  -  -
 -  #  -  -  -  -  -  -

julia> adjacentfilesquares(SQ_D4)
SquareSet:
 -  -  #  -  #  -  -  -
 -  -  #  -  #  -  -  -
 -  -  #  -  #  -  -  -
 -  -  #  -  #  -  -  -
 -  -  #  -  #  -  -  -
 -  -  #  -  #  -  -  -
 -  -  #  -  #  -  -  -
 -  -  #  -  #  -  -  -
```
