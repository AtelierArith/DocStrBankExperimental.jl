```
lc_analytic(::CrawfordMethod, InitialEffort, TotalUnits, Learning)
```

クローウフォードの学習曲線モデルを使用して累積コストを計算します。

式:     cost = Σ(i=1 to TotalUnits)[ InitialEffort * i ^ (log(Learning) / log(2)) ]
