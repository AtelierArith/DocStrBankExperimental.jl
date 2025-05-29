```
promotion(m::Move)
```

移動の昇格ピースタイプを見つけます。

この関数は、最初に `ispromotion` を使用して、その移動が昇格移動であるかどうかを判断した後にのみ使用してください。

# 例

```julia-repl
julia> promotion(Move(SQ_C7, SQ_C8, QUEEN))
QUEEN

julia> promotion(Move(SQ_B2, SQ_B1, KNIGHT))
KNIGHT
```
