分布の中央値、mad_sd、平均および標準偏差の要約を計算します。

```julia
model_summary(df, params; round_estimates, digits)

```

## 位置引数

```julia
* `df::DataFrame` # ドローを保持するDataFrame
* `params` # 含めるシンボルまたは文字列のベクター
```

## キーワード引数

```julia
* `round_estimates=true` # `digits` 小数点以下に丸める。
* `digits = 3` # 小数点以下の桁数
* `table_header_type=eltype(params)` # シンボルまたは文字列
```
