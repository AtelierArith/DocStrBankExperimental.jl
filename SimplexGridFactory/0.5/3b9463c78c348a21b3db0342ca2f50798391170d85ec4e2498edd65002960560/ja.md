```
facet!(builder,i1)
facet!(builder,i1,i2)
facet!(builder,i1,i2,i3,i4)
facet!(builder,vector_or_tuple)
facet!(builder, (x1,y1), (x2,y2))
facet!(builder, (x1,y1,z1), (x2,y2,z2),(x3,y3,z3))
```

[`point!`](@ref)によって返される対応する点インデックスを介してファセットを追加します。

2つの点のファセットは、2Dグリッド専用です。2つ以上の点を持つファセットは3Dグリッドで使用され、平面でなければなりません。
