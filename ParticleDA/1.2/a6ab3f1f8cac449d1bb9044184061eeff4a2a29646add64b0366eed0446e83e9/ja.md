```
MeanAndVarSummaryStat <: AbstractCustomReductionSummaryStat
```

カスタム削減に基づく要約統計タイプで、各状態次元の粒子アンサンブルの平均と分散を計算します。カスタム削減をサポートしていないCPUアーキテクチャでは、[`NaiveMeanAndVarSummaryStat`](@ref)を代わりに使用できます。
