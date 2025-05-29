```
cutord!(t::TPS{T}, t1::TPS{T}, order::Integer) where {T} -> t
```

指定された次数以上の `t1` の単項式を切り取ります。あるいは、`order` が負の場合は、次数が `abs(order)` 以下の単項式を切り取ります。`t` は結果に設定されます。例については `cutord` のドキュメントを参照してください。
