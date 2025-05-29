```
KHist(k::Int)
```

`k` 個のほぼ等間隔の点での一変量分布の確率密度を推定します。

参考文献: [https://www.jmlr.org/papers/volume11/ben-haim10a/ben-haim10a.pdf](https://www.jmlr.org/papers/volume11/ben-haim10a/ben-haim10a.pdf)

上記の参考文献との違いは、最小値と最大値が別のビンに統合されることが許可されていない点です。

# 例

```
o = fit!(KHist(25), randn(10^6))

# おおよその統計
using Statistics
mean(o)
var(o)
std(o)
quantile(o)
median(o)

using Plots
plot(o)
```
