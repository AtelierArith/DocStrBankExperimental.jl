```
refine_cell(cell::Cell, symprec=1e-5)
```

返された精製セル。

標準化された結晶構造は、対称性認識許容範囲内でわずかに歪んでいる非標準結晶構造から得られるか、原始ベクトルが異なる選択をされているなどします。この関数は現在、`to_primitive = false`および`no_idealize = false`を使用した`standardize_cell`のショートカットです。
