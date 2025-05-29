```
getord!(t::TPS{T}, t1::TPS{T}, order::Integer) where {T} -> t
```

指定された次数の `t1` から一つの同次多項式を抽出し、結果をその場で `t` に設定します。
