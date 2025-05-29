```
Ash(h::Union{KHist, Hist, ExpandingHist})
Ash(h::Union{KHist, Hist, ExpandingHist}, m::Int, kernel::Function)
```

`h`を基にした平均シフトヒストグラムを作成し、スムージングパラメータ`m`とカーネル関数`kernel`を使用します。組み込みカーネルは`OnlineStats.Kernels`モジュールで利用可能です。

# 例

```
using OnlineStats, Plots

o = fit!(Ash(ExpandingHist(1000)), randn(10^6))

plot(o)
plot(o, 20)
plot(o, OnlineStats.Kernels.epanechnikov, 4)
```
