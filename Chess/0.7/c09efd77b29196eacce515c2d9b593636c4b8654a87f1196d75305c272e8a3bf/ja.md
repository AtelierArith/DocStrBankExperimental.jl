```
bishops(b::Board)
```

どちらの色のビショップも含むマスの集合。

# 例

```julia-repl
julia> b = startboard();

julia> bishops(b) == SquareSet(SQ_C1, SQ_F1, SQ_C8, SQ_F8)
true
```
