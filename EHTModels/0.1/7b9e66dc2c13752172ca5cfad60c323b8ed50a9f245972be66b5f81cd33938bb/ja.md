```julia
struct Gaussian{T} <: EHTModels.GeometricModel
```

単位標準偏差とフラックスを持つガウス分布。デフォルトでは、Tが指定されていない場合、`Gaussian`は`Float64`にデフォルト設定されます。
