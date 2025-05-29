```
get_table_num(data, table_name, col_name, row_idx, yr_idx, hr_idx) -> num::Float64
```

`table[row_idx, col_idx][yr_idx, hr_idx]` から `Float64` を取得します。これは必要に応じて [`Container`](@ref) にインデックスを付け、`Float64` 列でも機能します。

関連する関数:

  * [`get_table_val(data, table_name, col_name, row_idx)`](@ref): テーブルから生の値を取得します（年/時間でインデックスを付けずに）。
  * [`get_num(data, name, yr_idx, hr_idx)`](@ref): `data` から `Float64` を取得し、年と時間でインデックスを付けます。
