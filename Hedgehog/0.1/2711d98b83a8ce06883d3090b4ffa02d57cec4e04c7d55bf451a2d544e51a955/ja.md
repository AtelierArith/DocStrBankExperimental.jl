```
yearfrac(p::AbstractTime)
```

`Period`オブジェクト（例：`Year(1)`、`Day(180)`）からACT/365年の割合を計算します。`CompoundPeriod`や日付も許可されており、グレゴリオ暦の年0からの時間の期間として解釈されます。期間が表す持続時間をミリ秒で計算し、`MILLISECONDS_IN_YEAR_365`で割ります。
