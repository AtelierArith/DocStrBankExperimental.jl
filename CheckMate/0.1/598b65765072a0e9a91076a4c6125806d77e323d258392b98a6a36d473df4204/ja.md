```
pass_rate(summary::CheckSummary, check_name::String)::Float64
```

特定のチェックの合格率を、合格した行の数に基づいて計算します。

# 引数

  * `summary::CheckSummary`: 複数のチェックの結果を含むサマリーオブジェクト。
  * `check_name::String`: 合格率を計算する特定のチェックの名前。

# 戻り値

指定されたチェックに合格した行の割合をパーセンテージで返し、小数点以下1桁に四捨五入します（0-100）。

# 例

```julia
rate = pass_rate(summary, "column_type_check")  # このチェックに95%の行が合格した場合、95.0を返します
```
