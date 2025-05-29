```
CovarianceMatrix(dd::DataFrame, error_if_incomplete::Bool = false)
```

シリアライズされた `CovarianceMatrix` を含む `DataFrame` を実際の CovarianceMatrix オブジェクトに変換します。

### 入力

  * `dd` - `DataFrame(covar::CovarianceMatrix, othercols::Dict = Dict{Symbol,Any}(); delete_duplicate_correlations::Bool = true)` 関数によって生成された形式の `DataFrame` 。
  * `error_if_incomplete` - true の場合、データが不十分なときにエラーをスローします。そうでない場合は、データが欠けている場所に NaN を挿入します。

### 戻り値

  * `CovarianceMatrix` 構造体。
