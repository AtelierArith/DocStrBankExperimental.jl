```
set_prop!(g, val)
set_prop!(g, v, val)
set_prop!(g, e, val)
set_prop!(g, s, d, val)
```

グラフ `g`、頂点 `v`、またはエッジ `e` の特定のプロパティ（頂点のデータ、エッジのID、グラフの最大ID）を値 `val` で設定（置き換え）します。頂点またはエッジが存在しない場合は false を返し、それ以外の場合は true を返します。
