```
upper_confidence_interval(stochasticmodel::StochasticModel{2}, decision::AbstractVector, sampler::AbstractSampler; kw...)
```

現在の信頼水準で、`sampler`によって誘導されるシナリオ分布における二段階`stochasticmodel`の`decision`の期待値の上限に対する信頼区間を生成します。

属性[`NumUpperTrials`](@ref)はサンプリングされたモデルの数であり、属性[`NumEvalSamples`](@ref)は評価モデルのサイズです。信頼水準は[`Confidence`](@ref)属性を通じて設定できます。

提供された`decision`は`stochasticmodel`で定義された意思決定変数と一致する必要があります。まだオプティマイザーが設定されていない場合（[`set_optimizer`](@ref]を参照）、`NoOptimizer`エラーがスローされます。
