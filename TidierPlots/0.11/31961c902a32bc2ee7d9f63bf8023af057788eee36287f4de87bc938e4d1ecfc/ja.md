```
label_currency(;kwargs...)
```

数値を通貨文字列に変換します。

# 引数

  * `kwargs`: `label_number` に渡される追加のキーワード引数。

# 例

```julia
labeler = label_currency()
labeler([100, 200.75]) # ["$100", "$200.75"]
```
