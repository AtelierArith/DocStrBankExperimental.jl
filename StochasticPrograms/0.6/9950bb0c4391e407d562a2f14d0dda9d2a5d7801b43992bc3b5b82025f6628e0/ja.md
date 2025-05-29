```
optimize!(stochasticmodel::StochasticModel, sampler::AbstractSampler; crash::AbstractCrash = Crash.None(), kw...)
```

基礎となるシナリオ分布が `sampler` によって推測されるとき、`stochasticmodel` をおおよそ最適化します。まだオプティマイザーが設定されていない場合（[`set_optimizer`](@ref) を参照）、`NoOptimizer` エラーがスローされます。
