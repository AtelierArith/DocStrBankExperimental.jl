```
LocalFilters.unit_range(r::Union{AbstractRange{<:Integer},CartesianIndices})
```

は `r` を `Int` 値の単位ステップインデックス範囲に変換します。`r` は線形またはカートesianインデックス範囲である可能性があります。`r` が線形範囲の場合、そのステップの絶対値は 1 でなければなりません。

```
LocalFilters.unit_range(start::Integer, stop::Integer)
```

は `Int` 値の単位ステップ範囲 `Int(start):Int(stop)` を生成します。
