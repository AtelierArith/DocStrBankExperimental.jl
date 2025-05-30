```
sample(
    rng::Random.AbatractRNG=Random.default_rng(),
    model::AbstractModel,
    sampler::AbstractSampler,
    N_or_isdone;
    kwargs...,
)
```

`model` からマルコフ連鎖モンテカルロ `sampler` を使用してサンプルを取得し、サンプルを返します。

`N_or_isdone` が `Integer` の場合、正確に `N_or_isdone` サンプルが返されます。

そうでない場合、収束基準 `N_or_isdone` が `true` を返すまでサンプリングが行われます。収束基準は次のシグネチャを持つ関数である必要があります。

```julia
isdone(rng, model, sampler, samples, state, iteration; kwargs...)
```

ここで、`state` と `iteration` はそれぞれサンプラーの現在の状態とイテレーションです。サンプリングを終了すべきときに `true` を返し、そうでない場合は `false` を返す必要があります。

# キーワード引数

一般的なキーワード引数については、https://turinglang.org/AbstractMCMC.jl/dev/api/#Common-keyword-arguments を参照してください。
