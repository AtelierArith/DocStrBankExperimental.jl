```
lefschetz_topboundary(lc::LefschetzComplex, subcomp::Vector{Int})
```

Lefschetz複体部分集合の位相的境界を計算します。

境界演算子を介して定義される代数的境界とは対照的に、この関数はLefschetz複体が有限位相空間として解釈される場合に、`subcomp`で指定されたLefschetz複体部分集合の境界を計算します。言い換えれば、位相的境界は部分集合の閉包と内部の集合の差です。
