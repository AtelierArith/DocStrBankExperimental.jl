```julia
modelage(mineral::ZirconFT, Tsteps, am::ZirconAnnealingModel)
modelage(mineral::MonaziteFT, Tsteps, am::MonaziteAnnealingModel)
modelage(mineral::ApatiteFT, Tsteps, am::ApatiteAnnealingModel)
```

与えられたt-T経路（時間のための`mineral.tsteps`と温度のための`Tsteps`で指定され、時間分解能は`step(mineral.tsteps)`）を経験したアパタイトの予測された核分裂トラック年齢を計算します。また、与えられたアニーリングモデルパラメータ`am`も考慮します。

考えられるアニーリングモデルのタイプと、それぞれが実装する方程式の参照は以下の通りです。 `Ketcham1999FC`       Ketcham et al. 1999のファニング曲線アパタイトモデル (doi: 10.2138/am-1999-0903)   `Ketcham2007FC`       Ketcham et al. 2007のファニング曲線アパタイトモデル (doi: 10.2138/am.2007.2281)   `Yamada2007PC`        Yamada et al. 2007の平行曲線ジルコンモデル (doi: 10.1016/j.chemgeo.2006.09.002)   `Guenthner2013FC`     Guenthner et al. 2013のファニング曲線ジルコンモデル (doi: 10.2475/03.2013.01)   `Jones2021FA`         Jones et al. 2021から適応されたファニングアレニウス（ファニング線形）モデル (doi: 10.5194/gchron-3-89-2021)
