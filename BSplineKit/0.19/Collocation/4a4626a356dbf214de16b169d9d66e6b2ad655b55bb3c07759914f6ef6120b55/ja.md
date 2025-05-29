```
collocation_matrix!(
    C::AbstractMatrix{T}, B::AbstractBSplineBasis, x::AbstractVector,
    [deriv::Derivative = Derivative(0)]; clip_threshold = eps(T))
```

事前に割り当てられたコレクション行列を埋めます。

詳細については[`collocation_matrix`](@ref)を参照してください。
