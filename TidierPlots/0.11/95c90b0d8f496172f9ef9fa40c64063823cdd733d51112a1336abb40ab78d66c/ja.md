```
label_scientific(;kwargs...)
```

数値を科学的表記の文字列に変換します。

# 引数

  * `kwargs`: `label_number` に渡される追加のキーワード引数。

# 例

```julia
labeler = label_scientific()
labeler([1000, 2000000]) # ["1e+03", "2e+06"]
```
