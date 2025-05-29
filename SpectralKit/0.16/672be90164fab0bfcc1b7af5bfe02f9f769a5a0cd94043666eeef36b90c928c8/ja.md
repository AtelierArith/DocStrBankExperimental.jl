```julia
struct Chebyshev{K<:SpectralKit.AbstractGrid} <: SpectralKit.UnivariateBasis
```

最初の `N` 個の第一種チェビシェフ多項式は、`[-1,1]` 上で定義されています。
