```
kings(b::Board)
```

どちらの色のキングが含まれているマスの集合。

# 例

```julia-repl
julia> b = startboard();

julia> kings(b) == SquareSet(SQ_E1, SQ_E8)
true
```
