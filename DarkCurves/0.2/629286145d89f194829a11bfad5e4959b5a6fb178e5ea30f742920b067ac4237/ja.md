```
curve_point_type(::Type{<:EllipticCurve})
```

指定された型のオブジェクト（[`EllipticCurve`](@ref)の型）に対する曲線点の型（[`EllipticCurvePoint`](@ref)のサブタイプ）を返します。

この型のオブジェクトは、`zero()`, `iszero()`, `one()`, `rand()`, `+`, `-`, `==`, `*`（スカラー型による）をサポートします。

基準点は`one()`によって返され、無限点は`zero()`によって返されます。
