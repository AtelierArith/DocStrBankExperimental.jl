```
ranksquares(r::SquareRank)
ranksquares(s::Square)
```

提供されたランクのすべての正方形のセット。

# 例

```julia-repl
julia> ranksquares(RANK_2) == SS_RANK_2
true

julia> ranksquares(SQ_C5) == SS_RANK_5
true
```
