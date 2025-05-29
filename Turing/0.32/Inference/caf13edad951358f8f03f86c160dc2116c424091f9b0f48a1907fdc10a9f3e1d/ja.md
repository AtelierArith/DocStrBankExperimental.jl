```julia
struct PG{space, R} <: Turing.Inference.ParticleInference
```

パーティクルギブスサンプラー。

# フィールド

  * `nparticles::Int64`: パーティクルの数。
  * `resampler::Any`: リサンプリングアルゴリズム。
