```julia
modellength(track::ApatiteTrackLength, Tsteps, am::ApatiteAnnealingModel)
```

与えられたt-T経路（`track.tsteps`による時間と`Tsteps`による温度で指定され、`step(mineral.tsteps)`の時間分解能で）を経験したアパタイトの核分裂トラック長の分布の予測平均と標準偏差を計算します。また、与えられたアニーリングモデルパラメータ`am`も考慮します。

考えられるアニーリングモデルのタイプと、それぞれが実装する方程式の参照には以下が含まれます。`Ketcham1999FC` Ketcham et al. 1999のファニング曲線アパタイトモデル (doi: 10.2138/am-1999-0903) `Ketcham2007FC` Ketcham et al. 2007のファニング曲線アパタイトモデル (doi: 10.2138/am.2007.2281)
