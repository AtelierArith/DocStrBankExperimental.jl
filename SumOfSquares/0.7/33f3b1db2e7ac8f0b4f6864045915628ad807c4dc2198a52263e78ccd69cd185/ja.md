```
struct PSDMatrixInnerCone{MCT <: MOI.AbstractVectorSet} <: PolyJuMP.PolynomialSet
end
```

任意の `x` に対して半正定値である多項式行列 `P(x)` の円錐の内近似であり、$n \times n$ 多項式行列の集合によって定義され、$y^\top P(x) y$ が `NonnegPolyInnerCone{MCT}` に属する多項式である。ここで、$y$ は $n$ 個の補助多項式変数のベクトルである。
