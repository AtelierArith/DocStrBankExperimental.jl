```
TupleSetData
```

タプルセットをパラメータ化するデータ。

# フィールド

  * `tuple_set::Vector{Vector{Int}}`: 繰り返されないタプルからなる主要なタプルセット。
  * `repeat_tuple_set::Vector{Vector{Int}}`: `repeat_numbers` に従ってタプルが繰り返される繰り返しタプルセット。
  * `repeat_numbers::Vector{Int}`: 繰り返しタプルセット `repeat_tuple_set` のタプルの繰り返し回数。
  * `repeat_indices::Vector{Tuple{Int, Int}}`: 繰り返しタプルセット `repeat_tuple_set` と `repeat_numbers` からのインデックスペア（`repeat_tuple`、`repeat_number`）で、すべてのインデックスペアに対して `repeat_tuple` が `repeat_number` 回繰り返されるように構成される。
