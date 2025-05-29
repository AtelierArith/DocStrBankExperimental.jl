```
sample(sampler::AbstractSampler, x::Real)
sample(sampler::AbstractSampler, x::Real, y::Real)
sample(sampler::AbstractSampler, x::Real, y::Real, z::Real)
sample(sampler::AbstractSampler, x::Real, y::Real, z::Real, w::Real)
```

`sampler`から提供された座標でサンプリングします。座標の数はサンプラータイプの次元数と一致する必要があります。
