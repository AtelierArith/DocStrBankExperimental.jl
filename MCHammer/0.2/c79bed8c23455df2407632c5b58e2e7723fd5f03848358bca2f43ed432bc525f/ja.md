```
GBMM_Sim(LastValue, ReturnsMean, ReturnsStd, PeriodsToForecast; trials=1)
```

GBMM_Simは、最後のデータポイントを使用して複数のランダムウォークを生成し、平均と標準偏差を提供する必要があります。

**LastValue**: ランダムウォークの基にする最も最近のデータポイント。

**ReturnsMean and ReturnsStd** : リターンの歴史的平均と標準偏差

**PeriodsToForecast**は整数 >1

**trials**: シミュレーションされた時系列配列を生成するためのものです。
