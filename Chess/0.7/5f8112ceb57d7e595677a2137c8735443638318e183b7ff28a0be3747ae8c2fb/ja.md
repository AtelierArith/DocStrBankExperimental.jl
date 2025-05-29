```
bishoplike(b::Board)
```

ビショップのような色の駒が含まれるマスの集合。

ビショップのような駒とは、ビショップのように動ける駒、すなわちビショップとクイーンです。

# 例

```julia-repl
julia> b = startboard();

julia> bishoplike(b) == SquareSet(SQ_C1, SQ_D1, SQ_F1, SQ_C8, SQ_D8, SQ_F8)
true
```
