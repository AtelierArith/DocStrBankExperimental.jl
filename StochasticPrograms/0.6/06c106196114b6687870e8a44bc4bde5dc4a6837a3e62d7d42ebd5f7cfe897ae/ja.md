```
EEV(stochasticmodel::StochasticModel{2}, sampler::AbstractSampler)
```

現在の信頼レベルに対して、`sampler`によって誘導されるシナリオ分布の上で、二段階の`stochasticmodel`の**期待値の期待値**（`EEV`）を概算します。

属性[`NumEEVSamples`](@ref)は、eev計算に使用されるサンプルモデルのサイズです。信頼レベルは、[`Confidence`](@ref)属性を通じて設定できます。

サンプルベースの最適化ツールがまだ設定されていない場合（[`set_optimizer`](@ref]を参照）、`NoOptimizer`エラーがスローされます。

関連情報: [`EVP`](@ref), [`EV`](@ref)
