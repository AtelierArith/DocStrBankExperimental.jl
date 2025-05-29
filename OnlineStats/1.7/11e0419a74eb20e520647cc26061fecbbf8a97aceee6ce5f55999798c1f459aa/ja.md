```
Trace(stat, b=500, f=value)
```

`b` 個の "スナップショット" を保存する OnlineStat のラッパー (OnlineStat の固定コピー)。スナップショットは、0 と現在の `nobs` の間でほぼ等間隔で取得されます。主な使用ケースは、観測が追加されるにつれて状態の変化を視覚化することです。

# 例

```
using OnlineStats, Plots

o = Trace(Mean(), 10)

fit!(o, 1:100)

OnlineStats.snapshots(o)

plot(o)
```
