```
constraints(R::AbstractBSplineBasis) -> (left, right)
constraints(A::RecombineMatrix) -> (left, right)
```

境界で基底が満たす制約（同次境界条件）を返します。

制約はタプル `(left, right)` として返され、各境界で満たされるBCを示します。各要素は、BCを指定する微分演算子のタプルです。

例えば、左境界でディリクレ条件とノイマン条件の両方が満たされている場合、`left = (Derivative(0), Derivative(1))` となります。

[`BSplineBasis`](@ref) のような非再結合基底の場合、これは空のタプルのタプル `((), ())` を返します。境界のいずれでもBCは満たされていないためです。
