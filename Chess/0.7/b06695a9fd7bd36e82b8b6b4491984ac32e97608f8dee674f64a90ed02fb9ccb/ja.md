```
shift_w(ss::SquareSet)
```

正方形セットを「西」方向に1ステップ移動します。

ボードの端から移動した正方形は消えます。

```julia-repl
julia> shift_w(SS_FILE_C) == SS_FILE_B
true

julia> shift_w(SquareSet(SQ_C5, SQ_B6, SQ_A7)) == SquareSet(SQ_B5, SQ_A6)
true
```
