```
GBMM(LastValue, ReturnsMean, ReturnsStd, PeriodsToForecast; rng::Any="none")
```

GBMMは、最後のデータポイントを使用してランダムウォークを生成し、平均と標準偏差を提供する必要があります。

**LastValue**: ランダムウォークの基にする最も最近のデータポイント。

**ReturnsMean and ReturnsStd** : リターンの歴史的平均と標準偏差

**PeriodsToForecast** は整数 >1

**rng** はnoneに設定すると完全にランダムです。結果をシードするために使用したいrngを指定できます。例えば、MersenneTwister(1234)などです。
