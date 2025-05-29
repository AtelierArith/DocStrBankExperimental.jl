```
sample(
    rng::Random.AbstractRNG=Random.default_rng(),
    model::AbstractModel,
    sampler::AbstractSampler,
    parallel::AbstractMCMCEnsemble,
    N::Integer,
    nchains::Integer;
    kwargs...,
)
```

`model`から`sampler`を使用して`nchains`のモンテカルロマルコフ連鎖を並行してサンプリングし、それらを単一の連鎖に結合します。

# キーワード引数

一般的なキーワード引数については、https://turinglang.org/AbstractMCMC.jl/dev/api/#Common-keyword-arguments を参照してください。
