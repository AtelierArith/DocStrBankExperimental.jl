```
SamplingContext(
        [rng::Random.AbstractRNG=Random.default_rng()],
        [sampler::AbstractSampler=SampleFromPrior()],
        [context::AbstractContext=DefaultContext()],
)
```

モデルを実行する際に、`sampler`を使用してパラメータをサンプリングできるコンテキストを作成します。`context`は、モデルを実行する際に返される対数密度がどのように計算されるかを決定します。

参照: [`DefaultContext`](@ref), [`LikelihoodContext`](@ref), [`PriorContext`](@ref)
