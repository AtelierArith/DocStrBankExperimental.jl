```
evaluate_decision(stochasticmodel::StochasticModel{2}, decision::AbstractVector, sampler::AbstractSampler; kw...)
```

現在の信頼水準で、`sampler`によって誘導されたシナリオ分布における`decision`での二段階`stochasticmodel`の目的の統計的推定値を信頼区間の形で返します。

言い換えれば、サンプルモデルで`decision`を評価し、評価のサンプル分散を使用して信頼区間を生成します。信頼水準は[`Confidence`](@ref)属性を通じて設定でき、サンプルサイズは[`NumEvalSamples`](@ref)属性を通じて設定できます。

提供された`decision`は、`stochasticmodel`で定義された意思決定変数と一致する必要があります。サンプルベースの最適化プログラムがまだ設定されていない場合（[`set_optimizer`](@ref]を参照）、`NoOptimizer`エラーがスローされます。

参照: [`confidence_interval`](@ref)
