```
rooklike(b::Board)
```

ルークのような色の駒が含まれるマスの集合。

ルークのような駒は、ルークのように動くことができる駒、すなわちルークとクイーンです。

# 例

```julia-repl
julia> b = startboard();

julia> rooklike(b) == SquareSet(SQ_A1, SQ_D1, SQ_H1, SQ_A8, SQ_D8, SQ_H8)
true
```
