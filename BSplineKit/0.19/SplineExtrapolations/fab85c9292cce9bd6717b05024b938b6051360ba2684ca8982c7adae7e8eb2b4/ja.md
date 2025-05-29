```
extrapolate(S::Union{Spline, SplineWrapper}, method::AbstractExtrapolationMethod)
```

与えられたスプライン `S`（補間の結果であることもできます）から [`SplineExtrapolation`](@ref) を構築します。
