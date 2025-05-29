```
settypes!(lines::LineIndex, d::Union{Dict{Symbol, DataType}, Dict{Symbol, UnionAll}, Dict{Symbol, Union}})
```

列の型を手動で設定します。`d`は、キーが列名に対応する`Symbol`であり、値がデータ型である`Dict`です。
