```
get_num(data, variable_name, yr_idx, hr_idx) -> num::Float64

get_num(table, col_name, row_idx, yr_idx, hr_idx) -> num::Float64
```

`data[variable_name]` から年と時間でインデックス付けされた `Float64` を取得します。 [`Container`](@ref)s と `Number`s に対して機能します。

関連する関数:

  * [`get_table_val(data, table_name, col_name, row_idx)`](@ref): テーブルから生の値を取得します（年/時間でインデックス付けせず）。
  * [`get_table_num(data, table_name, col_name, row_idx, yr_idx, hr_idx)`](@ref): `data[variable_name]` から年と時間でインデックス付けされた `Float64` を取得します。
  * [`get_val(data, variable_name)`](@ref): 行、年、または時間でインデックス付けせずに、data[variable_name] から値を取得します。
