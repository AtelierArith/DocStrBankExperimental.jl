```
galerkin_projection!(
    f, φ::AbstractVector, B::AbstractBSplineBasis, [deriv = Derivative(0)],
)
```

ガレルキン射影を計算します $φ_i = ⟨ b_i, f ⟩$。

詳細については [`galerkin_projection`](@ref) を参照してください。
