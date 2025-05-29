```
read_scenarios(filepath::String, sheet=1; kwargs...)
```

シナリオを `DataFrame` に読み込むテーブルファイルを読み込みます。

引数:

  * `filepath` : テーブルファイルへのパス。".csv" および ".xlsx" ファイルをサポートしています。
  * `sheet` : ".xlsx" ファイルの場合のシート番号。デフォルトは `1` です。
  * kwargs : `CSV.File` または `XLSX.readtable` によってサポートされるその他の引数。
