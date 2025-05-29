```julia
struct InteriorGrid2 <: SpectralKit.AbstractGrid
```

内部点を持つグリッドで、ネストされたときに`InteriorGrid`よりも小さなグリッドを生成します。エンドポイントが削除された`EndpointGrid`に相当します。
