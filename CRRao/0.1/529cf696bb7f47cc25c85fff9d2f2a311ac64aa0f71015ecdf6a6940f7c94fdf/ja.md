```julia
BPTest(container::FrequentistRegression, data::DataFrame)
```

ブラシ-ペガンテストを実行します。このテストは線形回帰でのみ機能します。

# 例

```julia
using CRRao, RDatasets, StatsModels

# データセットを取得
mtcars = dataset("datasets", "mtcars")

# モデルを訓練
container = fit(@formula(MPG ~ HP + WT + Gear), mtcars, LinearRegression())

# BPTestを取得
BPTest(container, mtcars)
```
