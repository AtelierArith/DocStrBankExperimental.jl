```
label_percent(;kwargs...)
```

数値をパーセンテージ文字列に変換します。

# 引数

  * `kwargs`: `label_number` に渡される追加のキーワード引数。

# 例

```julia
labeler = label_percent()
labeler([0.1, 0.256]) # ["10%", "25.6%"]
```
