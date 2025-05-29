```
NaiveMeanSummaryStat <: AbstractSumReductionSummaryStat
```

粒子アンサンブルの各状態次元の平均を計算するサムリダクションベースの要約統計タイプです。平均は、各ランクでの粒子値の合計と粒子数を直接累積することによって計算されます。使用中のCPUアーキテクチャがカスタムリダクションをサポートしている場合は、より数値的に安定した [`MeanSummaryStat`](@ref) を代わりに使用するべきです。
