```
MeanSummaryStat <: AbstractCustomReductionSummaryStat
```

カスタム削減に基づく要約統計タイプで、各状態次元の粒子アンサンブルの平均を計算します。カスタム削減をサポートしていないCPUアーキテクチャでは、[`NaiveMeanSummaryStat`](@ref)を代わりに使用できます。
