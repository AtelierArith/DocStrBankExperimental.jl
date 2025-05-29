```
lc_analytic(::WrightMethod, InitialEffort, TotalUnits, Learning)
```

ワイツの学習曲線モデルを使用して累積コストを計算します。

式:     cost = InitialEffort * (TotalUnits ^ ((log(Learning) / log(2)) + 1))
