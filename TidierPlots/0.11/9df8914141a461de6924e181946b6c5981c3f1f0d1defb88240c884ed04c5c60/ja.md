```
label_ordinal(;kwargs...)
```

数値を序数の文字列に変換します（例：1st、2nd、3rd）。

# 引数

  * `kwargs`: `label_number` に渡される追加のキーワード引数。

# 例

```julia
labeler = label_ordinal()
labeler([1, 2, 3]) # ["1st", "2nd", "3rd"]
```
