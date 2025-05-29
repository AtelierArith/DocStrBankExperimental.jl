```
get_table(data, table_name, conditions...) -> subtable::SubDataFrame
```

テーブル `table_name` のサブセットを返します。行が `conditions` を満たす場合です。条件は一般的に `<column name> => value` からなる `Pair` です。サポートされている条件の例は以下の通りです：

  * `:genfuel => "ng"` - `row.genfuel == "ng"` であるすべての行
  * `"bus_idx" => 1` - `row.bus_idx == 1` であるすべての行。列名は String または Symbol であることに注意してください
  * `:bus_idx  => "1"` - `row.bus_idx == 1` であるすべての行。これは String ですが、比較のために table.bus_idx の eltype に変換されます
  * `:year_on  => ("y2022", "y2030")` - `row.year_on` が "y2022" と "y2030" の間（両端を含む）であるすべての行。分数年にも対応しています。
  * `:genfuel => ["ng", "solar", "wind"]` - `row.genfuel` が "ng"、"solar"、または "wind" のいずれかであるすべての行
  * `:emis_co2 => f::Function` - f(row.emis_co2) が `true` を返すすべての行。例えば `>(0)` や `x->(0<x<=0.5)` などです。
