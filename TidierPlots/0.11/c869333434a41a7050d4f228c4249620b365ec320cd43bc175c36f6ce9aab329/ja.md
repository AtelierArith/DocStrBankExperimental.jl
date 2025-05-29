```
label_log(;base=10, kwargs...)
```

指定された基数で数値を対数文字列に変換します。

# 引数

  * `base`: 対数の基数。
  * `kwargs`: `label_number` に渡される追加のキーワード引数。

# 例

```julia
labeler = label_log(base=10)
labeler([10, 100]) # ["10^1", "10^2"]
```
