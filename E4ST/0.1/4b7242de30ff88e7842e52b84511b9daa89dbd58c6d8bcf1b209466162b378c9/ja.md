```
struct YearlyTable <: Modification

YearlyTable(;name, table_name, groupby=Symbol[], group_hours_by=Symbol[])
```

この修正は、シミュレーション内の各年のための集約テーブルを作成します。これは、[`get_results_formulas(data, table_name)`](@ref) にリストされているすべての結果式を含み、`groupby` の列名でグループ化されます。時間は `group_hours_by` フィールドの列によってグループ化されます。

# フィールド:

  * `name` - 修正の名前（このフィールドを設定ファイルで指定する必要はありません）。出力されるテーブルは [`get_out_path(config, "<name>_<year>.csv")`](@ref) に保存されます。
  * `table_name` - エクスポートするテーブルの名前。すなわち `gen`、`bus`、または `branch`
  * `groupby = Symbol[]` - `table_name` で指定されたテーブルのグループ化する列の名前。すなわち `state`、`nation`、`genfuel`、`gentype` など。全体のテーブルを1行にまとめるには空白のままにします。グループ化を防ぎ、すべての行を表示するには `:` を指定します。
  * `group_hours_by = Symbol[]` - グループ化する時間テーブルの列の名前。すなわち `season`。全体のテーブルをまとめるには空白のままにします。グループ化を防ぎ、すべての時間を表示するには `:` を指定します。
