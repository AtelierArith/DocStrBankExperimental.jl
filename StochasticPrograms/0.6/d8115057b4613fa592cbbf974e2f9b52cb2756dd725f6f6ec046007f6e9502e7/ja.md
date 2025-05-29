```
EVPI(stochasticmodel::StochasticModel{2}, sampler::AbstractSampler)
```

二段階の `stochasticmodel` の**完全情報の期待値**（`EVPI`）を、`sampler` によって誘発されるシナリオ分布に対する現在の信頼レベルでおおよそ計算します。

言い換えれば、`VRP` と `EWS` の周りの信頼区間を計算します。それらが重ならない場合、EVPI は統計的に有意であり、信頼区間が計算されて返されます。

属性 [`NumSamples`](@ref) は、区間を生成するために使用されるサンプルモデルのサイズであり、一般的にそのタイトさを決定します。属性 [`NumLowerTrials`](@ref) は下限計算に使用されるサンプルモデルの数であり、属性 [`NumUpperTrials`](@ref) は上限計算に使用されるサンプルモデルの数です。属性 [`NumEvalSamples`](@ref) は上限計算に使用されるサンプルモデルのサイズです。信頼レベルは、属性 [`Confidence`](@ref) を通じて設定できます。

サンプルベースの最適化プログラムがまだ設定されていない場合（[`set_optimizer`](@ref) を参照）、`NoOptimizer` エラーがスローされます。

関連情報: [`VRP`](@ref), [`EWS`](@ref), [`VSS`](@ref)
