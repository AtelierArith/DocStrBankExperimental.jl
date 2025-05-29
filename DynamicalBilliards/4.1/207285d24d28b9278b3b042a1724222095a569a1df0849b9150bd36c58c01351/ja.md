```
billiard_mushroom(sl = 1.0, sw = 0.2, cr = 1.0, sloc = 0.0; door = true)
```

茎の長さ `sl`、茎の幅 `sw`、および傘の半径 `cr` を持つキノコビリヤードを作成します。傘の中心（半円）は常に `[0, sl]` にあります。茎の中心は `sloc` に位置しています。

オプションで、最下部の `Wall` は `Door` です（[`escapetime`](@ref) を参照）。
