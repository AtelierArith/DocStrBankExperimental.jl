```
standardize_cell(cell::Cell; to_primitive=false, no_idealize=false, symprec=1e-5)
```

標準化されたセルを返します。

標準化された単位セルは、入力単位セル構造とその対称性検索によって見つかった対称性から生成されます。各空間群タイプの設定の選択は、[`get_dataset`](@ref)で説明されている通りです。
