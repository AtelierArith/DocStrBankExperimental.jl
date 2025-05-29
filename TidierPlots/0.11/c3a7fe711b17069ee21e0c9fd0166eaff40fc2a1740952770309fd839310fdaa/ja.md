```
label_date(;format="m/d/Y")
```

日付または日付時刻の値をフォーマットされた文字列に変換します。

# 引数

  * `format`: 日付フォーマット文字列。

# 例

```julia
labeler = label_date(format="Y-m-d")
labeler([Date(2020, 1, 1)]) # ["2020-1-1"]
```
