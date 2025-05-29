```
struct ConvexPolyInnerCone{MCT} <: PolyJuMP.PolynomialSet end
```

内包凸多項式の内近似は、そのヘッセ行列が集合 `PSDMatrixInnerCone{MCT}()` に属する多項式の集合によって定義される。
