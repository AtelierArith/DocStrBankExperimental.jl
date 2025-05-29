```
VRP(stochasticmodel::StochasticModel{2}, sampler::AbstractSampler; confidence = 0.95)
```

与えられた`confidence`レベルに対して、`stochasticmodel`の**再帰問題**（`VRP`）の値の周りの信頼区間を返します。

サンプルベースの最適化器がまだ設定されていない場合（[`set_optimizer`](@ref)を参照）、`NoOptimizer`エラーがスローされます。

関連情報: [`EVPI`](@ref), [`VSS`](@ref), [`EWS`](@ref)
