```
AbstractVariableRef
```

[`add_variable`](@ref)によって返される変数。タイプ`V<:AbstractVariableRef`の変数とタイプ`T`の係数を用いたアフィン（または二次）演算は、`GenericAffExpr{T,V}`（または`GenericQuadExpr{T,V}`）を生成します。
