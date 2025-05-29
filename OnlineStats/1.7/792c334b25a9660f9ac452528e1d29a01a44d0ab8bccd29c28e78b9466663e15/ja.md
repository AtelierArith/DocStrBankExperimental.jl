```
IndexedPartition(T, stat, b=100)
```

サイズ `b` のパーティションに対して `stat` を用いてデータを要約します。データは型 `T` の変数によってインデックス付けされています。

# 例

```
x, y = randn(10^5), randn(10^6)
o = IndexedPartition(Float64, KHist(10))
fit!(o, zip(x, y))

using Plots
plot(o)
```
