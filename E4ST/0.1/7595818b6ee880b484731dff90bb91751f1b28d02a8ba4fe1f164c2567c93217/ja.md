```
parse_comparisons(row::DataFrameRow) -> pairs
```

別のテーブルの行をフィルタリングするために使用されるペアのセットを返します。行の以下のプロパティを探します：

  * `area, subarea` - 行に空でないエリアとサブエリアがある場合、比較 `row.area=>row.subarea` を解析します。
  * `filter_` - 行に空でない `filter_`（すなわち `filter1`、`filter2`）の値がある場合、[`parse_comparison`](@ref) を介して比較を解析します。
  * `genfuel` - 行に空でない `genfuel` がある場合、各行の `genfuel` がこの値と等しいことを確認する比較を追加します。
  * `gentype` - 行に空でない `gentype` がある場合、各行の `gentype` がこの値と等しいことを確認する比較を追加します。
  * `load_type` - 行に空でない `load_type` がある場合、各行の `load_type` がこの値と等しいことを確認する比較を追加します。
