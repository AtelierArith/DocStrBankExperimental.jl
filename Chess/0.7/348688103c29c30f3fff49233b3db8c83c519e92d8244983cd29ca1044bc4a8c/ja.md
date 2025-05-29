```
isempty(ss::SquareSet)
```

正方形集合が空集合であるかどうかを判断します。

# 例

```julia-repl
julia> isempty(SS_RANK_1)
false

julia> isempty(SS_EMPTY)
true

julia> isempty(SS_RANK_1 ∩ SS_RANK_2)
true
```
