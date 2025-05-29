```julia
struct EndpointGrid <: SpectralKit.AbstractGrid
```

エンドポイントを含むグリッド（例：ガウス・ロバット）。

!!! note
    小さな次元の場合、エンドポイントを含まないグリッドにフォールバックすることがあります。

