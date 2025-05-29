```
rooks(b::Board)
```

どちらの色のルークが含まれているマスの集合。

# 例

```julia-repl
julia> b = startboard();

julia> rooks(b) == SquareSet(SQ_A1, SQ_H1, SQ_A8, SQ_H8)
true
```
