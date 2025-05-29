```julia
struct MRing{T, V<:Union{AbstractArray{T, 1}, NTuple{N, T} where {N, T}}} <: VLBISkyModels.GeometricModel{T}
```

m-ring 幾何モデル。これは、角度構造がフーリエ展開によって与えられる無限に薄い単位フラックスデルタリングです。すなわち、

```
I(r,θ) = (2π)⁻¹δ(r-1)∑ₙ(αₙcos(nθ) - βₙsin(nθ))
```

型の `N` はフーリエ展開の次数を定義します。

# フィールド

  * `α`: 実フーリエモード係数
  * `β`: 虚フーリエモード係数
