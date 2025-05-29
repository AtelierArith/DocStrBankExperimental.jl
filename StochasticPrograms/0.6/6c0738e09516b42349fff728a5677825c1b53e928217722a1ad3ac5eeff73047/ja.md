```
EWS(stochasticmodel::StochasticModel{2}, sampler::AbstractSampler)
```

現在の信頼水準に対する二段階`stochasticmodel`の**期待待機結果**(`EWS`)を、`sampler`によって誘発されるシナリオ分布にわたっておおよそ計算します。

属性[`NumEWSSamples`](@ref)は、区間を生成するために使用されるサンプルモデルのサイズであり、一般的にその厳密さを決定します。信頼水準は、[`Confidence`](@ref)属性を通じて設定できます。

サンプルベースの最適化器がまだ設定されていない場合（[`set_optimizer`](@ref]を参照）、`NoOptimizer`エラーがスローされます。

参照: [`VRP`](@ref), [`WS`](@ref)
