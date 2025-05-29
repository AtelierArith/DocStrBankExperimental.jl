```
set_props!(g, dict)
set_props!(g, v, dict)
set_props!(g, e, dict)
set_props!(g, s, d, dict)
```

`dict` に含まれるプロパティをグラフ `g`、頂点 `v`、または辺 `e` に一括設定（マージ）します（オプションで、始点頂点 `s` と終点頂点 `d` で参照されます）。頂点または辺が存在しない場合は false を返します。
