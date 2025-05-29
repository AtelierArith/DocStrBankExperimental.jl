```julia
struct Ring{T} <: VLBISkyModels.GeometricModel{T}
```

無限に薄いリングモデルで、画像領域における表現は I(r,θ) = δ(r - 1)/2π であり、単位半径とフラックスデルタリングです。

デフォルトでは、`T` が指定されていない場合、`Gaussian` は `Float64` にデフォルト設定されます。
