```
assignCenInVal!(b::FloatingGTBasisFuncs{T, D}, center::AbstractVector{<:Real}) -> 
SpatialPoint{T, D}
```

`b.center`に保存されている`ParamBox`の入力値を変更します（つまり、出力値もマッピング関数に従って変更されます）。その後、変更された中心を返します。
