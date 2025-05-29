```julia
struct TVShift{T<:Real} <: TransformVariables.ScalarTransform
```

シフト変換 `x ↦ x + shift`。
