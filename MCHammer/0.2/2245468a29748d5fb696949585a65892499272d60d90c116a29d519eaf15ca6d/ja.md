```
GBMMfit(HistoricalData, PeriodsToForecast; rng="none")
```

GBMMfitは、履歴データのベクトルを使用して対数リターンを計算し、平均と標準偏差を使用してランダムウォークを予測します。セット内の最後のデータポイントを新しい予測の出発点として使用します。

**HistoricalData**: 履歴データを含むベクトル

**PeriodsToForecast**: 整数 >1

**rng**は、noneに設定すると完全にランダムになります。結果をシードするrngを指定できます。例: MersenneTwister(1234)
