```
JuMP.constraint_ref_with_index(
element::OptiElement, 
idx::MOI.ConstraintIndex{<:MOI.AbstractScalarFunction, <:MOI.AbstractScalarSet}
)
```

オプティグラフ要素と `MOI.ConstraintIndex` を与えると、`ConstraintRef` を返します。インデックスは、要素インデックスではなく、グラフバックエンドに対応するインデックスであることに注意してください。
