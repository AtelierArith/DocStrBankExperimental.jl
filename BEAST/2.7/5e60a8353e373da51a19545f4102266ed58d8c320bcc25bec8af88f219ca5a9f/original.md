````
struct DoubleLayerRotatedMW3D{T,K} <: MaxwellOperator3D{T,K}

Bilinear form given by:

```math
    α ∬_{Γ^2} k(x) ⋅ [n̂(x) × (∇G_γ(x-y) × j(y))]
```

with ``G_γ = e^{-γ|x-y|} / 4π|x-y|``
````

# Fields

  * `alpha::T`: Factor in front of bilinear form.
  * `gamma::K`: imaginary unit times the wavenumber.
