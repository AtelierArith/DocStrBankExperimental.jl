```
find_primitive(cell::Cell, symprec=1e-5)
```

入力ユニットセルの原始セルを見つけます。

この関数は、`to_primitive = true` および `no_idealize = false` の `standardize_cell` のショートカットです。
