````
struct DoubleLayerRotatedMW3D{T,K} <: MaxwellOperator3D{T,K}

双線形形式は次のように与えられます：

```math
    α ∬_{Γ^2} k(x) ⋅ [n̂(x) × (∇G_γ(x-y) × j(y))]
```

ここで ``G_γ = e^{-γ|x-y|} / 4π|x-y|``
````

# フィールド

  * `alpha::T`: 双線形形式の前にある係数。
  * `gamma::K`: 波数に対する虚数単位。
