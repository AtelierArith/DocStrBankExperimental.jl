```
Heatmap(xedges, yedges; left = true, closed = true)
Heatmap(itr; left = true, closed = true)
```

`xedges` と `yedges` によって作成されたビンパーティションを使用して二次元ヒストグラムを作成します。新しい観測値をフィッティングする際、最初の値は X に、2 番目の値は Y に関連付けられます。

  * `left` が true の場合、ビンは左閉じになります。
  * `closed` が true の場合、端のビンは閉じられます。詳細は [`Hist`](@ref) を参照してください。

# 例

```
using Plots

xy = zip(randn(10^6), randn(10^6))
o = fit!(HeatMap(-5:.1:5, -5:.1:5), xy)
plot(o)

xy = zip(1 .+ randn(10^6) ./ 10, randn(10^6))
o = HeatMap(xy)
plot(o, marginals=false)
plot(o)
```
