```
shift_n(ss::SquareSet)
```

正方形セットを「北」方向に1ステップ移動します。

ボードの端から移動した正方形は消えます。

```julia-repl
julia> shift_n(SS_RANK_2) == SS_RANK_3
true

julia> shift_n(SquareSet(SQ_D3, SQ_E4, SQ_F8)) == SquareSet(SQ_D4, SQ_E5)
true
```
