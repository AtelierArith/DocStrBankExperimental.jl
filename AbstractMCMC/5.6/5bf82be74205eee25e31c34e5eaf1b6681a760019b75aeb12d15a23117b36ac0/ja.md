```
sample(
    rng::Random.AbstractRNG=Random.default_rng(),
    logdensity,
    sampler::AbstractSampler,
    N_or_isdone;
    kwargs...,
)
```

`logdensity` 関数を [`LogDensityModel`](@ref) でラップし、結果のモデルを使用して `sample` を呼び出します。

`logdensity` 関数は [LogDensityProblems.jl](https://github.com/tpapp/LogDensityProblems.jl) インターフェースをサポートする必要があります。
