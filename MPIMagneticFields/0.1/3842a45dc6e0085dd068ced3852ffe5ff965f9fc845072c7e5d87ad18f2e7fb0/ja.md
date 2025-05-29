```julia
struct NegativeField{T<:MPIMagneticFields.AbstractMagneticField} <: MPIMagneticFields.AbstractNegativeField
```

負のフィールドのコンテナ。

このコンテナのフィールドは `field` の負の値として解釈されます。
