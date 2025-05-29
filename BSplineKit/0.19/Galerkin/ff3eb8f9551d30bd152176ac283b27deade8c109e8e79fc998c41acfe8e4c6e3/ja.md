```
galerkin_tensor!(
    A::BandedTensor3D,
    B::AbstractBSplineBasis,
    (D₁::Derivative, D₂::Derivative, D₃::Derivative),
)
```

3D ガレルキンテンソルをインプレースで計算します。

詳細については [`galerkin_tensor`](@ref) を参照してください。
