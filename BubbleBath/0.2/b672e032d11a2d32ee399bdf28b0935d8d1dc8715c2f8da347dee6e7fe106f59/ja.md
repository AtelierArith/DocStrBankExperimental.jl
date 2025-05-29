```
packing_fraction(radii::Vector{Real}, extent::NTuple{D,Real}) where D
```

半径 `radii` の球のコレクションのパッキング分数を、領域 `extent` で評価します。この測定は、球が重なっている場合や領域の境界を越えている場合には正確ではありません。
