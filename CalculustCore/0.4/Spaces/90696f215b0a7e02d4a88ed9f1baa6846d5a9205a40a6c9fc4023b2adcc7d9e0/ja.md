```
laplaceOp(V::AbstractSpace, discr::AbstractDiscretization)
```

ラプラス演算子: -Δ

`V` に対する負のラプラス演算子を離散化スキーム `discr` に基づいて返します。ラプラス演算子（ラプラシアン）は負定義演算子であるため、正定義演算子である負のラプラス演算子を返します。
