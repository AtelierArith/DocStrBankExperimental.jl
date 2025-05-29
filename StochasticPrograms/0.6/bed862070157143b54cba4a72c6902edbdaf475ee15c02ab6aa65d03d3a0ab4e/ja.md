```
VSS(stochasticmodel::StochasticModel{2}, sampler::AbstractSampler)
```

現在の信頼水準に対する二段階`stochasticmodel`の**確率的解の値**（`VSS`）を、`sampler`によって誘発されるシナリオ分布に対しておおよそ計算します。

言い換えれば、`EEV`と`VRP`の周りの信頼区間を計算します。それらが重ならない場合、VSSは統計的に有意であり、信頼区間が計算されて返されます。`Ñ`は、EEVの外部サンプル評価におけるサンプル数です。

属性[`NumSamples`](@ref)は、区間を生成するために使用されるサンプルモデルのサイズであり、一般的にそれがどれだけタイトであるかを決定します。同じサイズが期待値の決定を生成するために使用されます。属性[`NumLowerTrials`](@ref)は下限計算に使用されるサンプルモデルの数であり、属性[`NumUpperTrials`](@ref)は上限計算に使用されるサンプルモデルの数です。属性[`NumEvalSamples`](@ref)は上限計算に使用されるサンプルモデルのサイズであり、属性[`NumEEVSamples`]は`EEV`計算に使用されるサンプルモデルのサイズです。信頼水準は、属性[`Confidence`](@ref)を通じて設定できます。

サンプルベースの最適化プログラムがまだ設定されていない場合（[`set_optimizer`](@ref)を参照）、`NoOptimizer`エラーがスローされます。

参照: [`VRP`](@ref), [`EEV`](@ref), [`EVPI`](@ref)
