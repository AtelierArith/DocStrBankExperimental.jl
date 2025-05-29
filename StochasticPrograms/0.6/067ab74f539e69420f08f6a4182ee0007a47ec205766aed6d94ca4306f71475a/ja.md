```
gap(stochasticmodel::StochasticModel{2}, decision::UnionAbstractVector, sampler::AbstractSampler)
```

`decision`を使用した結果と、現在の信頼水準での二段階`stochasticmodel`の真の最適解との間のギャップに関する信頼区間を生成します。これは、`sampler`によって誘導されるシナリオ分布に基づいています。

属性[`NumSamples`](@ref)は、区間を生成するために使用されるサンプルモデルのサイズであり、一般的にその厳密さを決定します。属性[`NumLowerTrials`](@ref)は、下限計算に使用されるサンプルモデルの数であり、属性[`NumUpperTrials`](@ref)は、上限計算に使用されるサンプルモデルの数です。属性[`NumEvalSamples`](@ref)は、上限計算に使用されるサンプルモデルのサイズです。信頼水準は、属性[`Confidence`](@ref)を通じて設定できます。

提供された`decision`は、`stochasticmodel`で定義された意思決定変数と一致する必要があります。サンプルベースの最適化プログラムがまだ設定されていない場合（[`set_optimizer`](@ref)を参照）、`NoOptimizer`エラーがスローされます。
