```
get_table_val(data, table_name, col_name, row_idx) -> val
```

指定された列 `col_name` と行 `row_idx` のテーブルの値を返します。

関連する関数：

  * [`get_table_num(data, table_name, col_name, row_idx, yr_idx, hr_idx)`](@ref): 年と時間でインデックス付けされた `data[variable_name]` から `Float64` を取得します。
  * [`get_num(data, name, yr_idx, hr_idx)`](@ref): 年と時間でインデックス付けされた `data` から `Float64` を取得します。
  * [`get_val(data, variable_name)`](@ref): 行、年、または時間でインデックス付けされずに `data[variable_name]` から値を取得します。
