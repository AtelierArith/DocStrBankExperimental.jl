```
lower_confidence_interval(stochasticmodel::StochasticModel{2}, sampler::AbstractSampler; kw...)
```

現在の信頼レベルでの二段階`stochasticmodel`の真の最適値の下限に関する信頼区間を、`sampler`によって誘導されるシナリオ分布に対して生成します。

属性[`NumSamples`](@ref)は、区間を生成するために使用されるサンプルモデルのサイズであり、一般的にそのタイトさを決定します。属性[`NumLowerTrials`](@ref)は、サンプルモデルの数です。信頼レベルは、[`Confidence`](@ref)属性を通じて設定できます。

サンプルベースの最適化器がまだ設定されていない場合（[`set_optimizer`](@ref]を参照）、`NoOptimizer`エラーがスローされます。
