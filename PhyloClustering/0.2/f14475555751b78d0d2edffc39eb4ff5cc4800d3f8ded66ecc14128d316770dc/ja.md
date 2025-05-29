```
show_bipartition(n::Int64, idx::Int64)
```

与えられた数の分類群に対して、指定されたインデックスの二分割を表示します。

# 引数

  * `n`: 分類群の数。
  * `idx`: 表示する二分割。

# 出力

`n` 種の木の `idx` 番目の二分割。

# 例:

```jldoctest
julia> show_bipartition(4, 3)
idx	partition
3	4 | 1 2 3 
```
