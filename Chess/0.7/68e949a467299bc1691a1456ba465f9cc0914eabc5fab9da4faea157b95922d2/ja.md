```
shift_e(ss::SquareSet)
```

正方形セットを「東」方向に1ステップ移動します。

ボードの端から移動した正方形は消えます。

# 例

```julia-repl
julia> shift_e(SS_FILE_F) == SS_FILE_G
true

julia> shift_e(SquareSet(SQ_F5, SQ_G6, SQ_H7)) == SquareSet(SQ_G5, SQ_H6)
true
```
