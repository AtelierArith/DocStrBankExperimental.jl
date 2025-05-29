```
compute_result(data, table_name, result_name, idxs=(:), yr_idxs=(:), hr_idxs=(:))
```

テーブル `table_name` のテーブルインデックス `idxs`、年インデックス `yr_idxs`、および時間インデックス `hr_idxs` に対して、結果 `result_name` を計算します。結果を計算するための他の結果式を追加するには、[`add_results_formula!`](@ref) を参照してください。

必要に応じて、派生結果の結果も再帰的に計算されることに注意してください。

計算された結果が `NaN` の場合は、他の結果に「感染」しないように `0.0` を返します。
