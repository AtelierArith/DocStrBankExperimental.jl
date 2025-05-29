```julia
struct SMC{space, R} <: Turing.Inference.ParticleInference
```

逐次モンテカルロサンプラー。

# フィールド

  * `resampler::Any`
