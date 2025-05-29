```
SortByField(field::AbstractString; asc::Bool=true)
```

特定のフィールドをソートするための `Fitler` オブジェクトを作成します。

# 引数

  * `field::AbstractString`: ソートされるフィールド名

# キーワード

  * `asc::Bool`: 昇順でソートするかどうか、デフォルトは `true`

# 戻り値

  * `Fitler::AbstractFilter`
