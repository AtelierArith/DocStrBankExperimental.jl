```julia
struct Gaussian{T} <: VLBISkyModels.GeometricModel{T}
```

単位標準偏差とフラックスを持つガウス分布。

デフォルトでは、Tが指定されていない場合、`Gaussian`は`Float64`にデフォルト設定されます。
