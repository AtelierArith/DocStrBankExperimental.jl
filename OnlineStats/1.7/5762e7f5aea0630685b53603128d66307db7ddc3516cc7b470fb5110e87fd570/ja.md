```
KIndexedPartition(T, stat_init, k=100)
```

[`IndexedPartition`](@ref)と似ていますが、最初の変数を区間ではなくセントロイドによってインデックス付けします（[`KHist`](@ref)のように）。

  * 注: `stat_init`は関数である必要があります。例: `() -> Mean()`

# 例

```
using Plots

o = KIndexedPartition(Float64, () -> KHist(10))

fit!(o, zip(randn(10^6), randn(10^6)))

plot(o)
```
