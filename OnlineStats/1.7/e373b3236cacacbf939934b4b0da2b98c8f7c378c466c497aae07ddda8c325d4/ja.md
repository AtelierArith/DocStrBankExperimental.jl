```
Partition(stat)
Partition(stat, nparts)
```

データストリームを `nparts`（デフォルトは100）に分割し、各部分は `stat` によって要約されます。

# 例

```
o = Partition(Extrema())
fit!(o, cumsum(randn(10^5)))

using Plots
plot(o)
```
