```
confidence_interval(stochasticmodel::StochasticModel{2}, sampler::AbstractSampler)
```

二段階の `stochasticmodel` の真の最適値の周りに、`sampler` によって誘発されるシナリオ分布に対して SAA を使用して、`confidence` レベルで信頼区間を生成します。

属性 [`NumSamples`](@ref) は、区間を生成するために使用されるサンプルモデルのサイズであり、一般的にその厳密さを決定します。属性 [`NumLowerTrials`](@ref) は下限計算に使用されるサンプルモデルの数であり、属性 [`NumUpperTrials`](@ref) は上限計算に使用されるサンプルモデルの数です。属性 [`NumEvalSamples`](@ref) は上限計算に使用されるサンプルモデルのサイズです。信頼レベルは、属性 [`Confidence`](@ref) を通じて設定できます。

サンプルベースの最適化器がまだ設定されていない場合（[`set_optimizer`](@ref) を参照）、`NoOptimizer` エラーがスローされます。
