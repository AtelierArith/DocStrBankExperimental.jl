```
findanalyte(dt::AbstractDataTable{A}, analyte::B) where {A, B <: A}
findanalyte(dt::AbstractDataTable, analyte::Symbol)
```

`analyteobj(dt)` または `analytename(dt)` の最初の要素のインデックスを返します。その要素が `analyte` と等しい場合です。
