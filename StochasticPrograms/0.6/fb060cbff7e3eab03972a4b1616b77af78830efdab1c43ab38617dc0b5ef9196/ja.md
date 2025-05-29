```
upper_confidence_interval(stochasticmodel::StochasticModel{2}, sampler::AbstractSampler; kw...)
```

現在の信頼水準で、`sampler`によって誘導されるシナリオ分布における二段階`stochasticmodel`の真の最適値の上限に関する信頼区間を生成し、候補の意思決定を生成して評価します。

属性[`NumSamples`](@ref)は、候補の意思決定を生成するために使用されるサンプルモデルのサイズです。属性[`NumUpperTrials`](@ref)はサンプルモデルの数であり、属性[`NumEvalSamples`](@ref)は評価モデルのサイズです。信頼水準は、属性[`Confidence`](@ref)を通じて設定できます。

サンプルベースの最適化器がまだ設定されていない場合（[`set_optimizer`](@ref]を参照）、`NoOptimizer`エラーがスローされます。
