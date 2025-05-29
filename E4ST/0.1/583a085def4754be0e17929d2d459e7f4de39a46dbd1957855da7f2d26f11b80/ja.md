```
CreditByBenchmark(;gen_col, benchmark)
```

各発電機のクレジットを、その発電機の `gen_col` が `benchmark` と比較してどのようであるかに基づいて授与します。以下の式を使用します。

```
max(1.0 - (gen_row[gen_col] / benchmark), 0.0)
```

  * `gen_col::Symbol` - 比較する `gen` テーブルの列
  * `benchmark::Float64` - `gen_col` と同じ単位で比較するベンチマークレート。
