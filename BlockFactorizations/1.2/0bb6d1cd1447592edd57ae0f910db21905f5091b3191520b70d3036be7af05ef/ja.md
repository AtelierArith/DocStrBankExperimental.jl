```
BlockFactorization{T} <: Factorization{T}
```

行列または因子分解の行列 `A` のラッパー型で、`eltype(A) = T` であり、コンポーネント行列が結合されて単一の行列 `B` を形成するかのように振る舞います。`eltype(B) = T` です。
