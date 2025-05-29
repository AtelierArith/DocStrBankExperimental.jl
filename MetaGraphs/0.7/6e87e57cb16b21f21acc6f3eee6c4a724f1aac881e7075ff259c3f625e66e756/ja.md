```
set_prop!(g, prop, val)
set_prop!(g, v, prop, val)
set_prop!(g, e, prop, val)
set_prop!(g, s, d, prop, val)
```

グラフ `g`、頂点 `v`、または辺 `e` において、プロパティ `prop` を値 `val` で設定（置き換え）します（オプションで、始点頂点 `s` と終点頂点 `d` によって参照されます）。頂点または辺が存在しない場合は false を返し、それ以外の場合は true を返します。
