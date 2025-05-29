```
shift_s(ss::SquareSet)
```

正方形セットを「南」方向に1ステップ移動します。

ボードの端から移動した正方形は消えます。

# 例

```julia-repl
julia> shift_s(SS_RANK_3) == SS_RANK_2
true

julia> shift_s(SquareSet(SQ_C3, SQ_D2, SQ_E1)) == SquareSet(SQ_C2, SQ_D1)
true
```
