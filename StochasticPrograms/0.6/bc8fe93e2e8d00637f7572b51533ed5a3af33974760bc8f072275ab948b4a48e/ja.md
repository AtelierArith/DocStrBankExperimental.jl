```
load_model!(optimizer::AbstractSampledOptimizer, model::StochasticModel, x₀::AbstractVector)
```

確率モデルと初期決定 `x₀` で `optimizer` をインスタンス化します。

参照: [`optimize!`](@ref)
