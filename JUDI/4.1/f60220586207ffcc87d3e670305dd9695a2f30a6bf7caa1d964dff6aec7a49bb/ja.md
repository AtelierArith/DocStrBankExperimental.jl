```
judiProjection(geometry)
```

指定された位置でデータを制限または注入するためのソース/レシーバーの投影演算子。

# 例

`F` は `judiModeling` 型のモデリング演算子で、`q` は `judiVector` 型の地震源です:     Pr = judiProjection(rec_geometry)     Ps = judiProjection(q.geometry)     dobs = Pr*F*Ps'*q     qad = Ps*F'*Pr'*dobs
