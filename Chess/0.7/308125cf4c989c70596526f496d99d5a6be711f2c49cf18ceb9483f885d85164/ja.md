```
pawns(b::Board)
```

どちらの色のポーンも含むマスの集合。

# 例

```julia-repl
julia> b = startboard();

julia> pawns(b) == SS_RANK_2 ∪ SS_RANK_7
true
```
