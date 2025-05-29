```
label_pvalue(;precision=2, kwargs...)
```

p値をフォーマットし、非常に小さいまたは大きい値を特別な表記で処理します。

# 引数

  * `precision`: 小さい値のしきい値のための小数点以下の桁数。
  * `kwargs`: `label_number` に渡される追加のキーワード引数。

# 例

```julia
labeler = label_pvalue()
labeler([0.0001, 0.05, 0.9999]) # ["<0.01", "0.05", ">0.99"]
```
