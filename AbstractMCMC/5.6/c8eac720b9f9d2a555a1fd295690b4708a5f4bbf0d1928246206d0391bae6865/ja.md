```
sample(
    rng::Random.AbstractRNG=Random.default_rng(),
    logdensity,
    sampler::AbstractSampler,
    parallel::AbstractMCMCEnsemble,
    N::Integer,
    nchains::Integer;
    kwargs...,
)
```

`logdensity` 関数を [`LogDensityModel`](@ref) でラップし、結果のモデルを使って `sample` を呼び出します。

`logdensity` 関数は [LogDensityProblems.jl](https://github.com/tpapp/LogDensityProblems.jl) インターフェースをサポートする必要があります。
