```julia
adjr2(container::FrequentistRegression)
```

調整済み決定係数。`adjr2` メソッドを [StatsAPI.jl](https://github.com/JuliaStats/StatsAPI.jl) から拡張します。

# 例

```julia
using CRRao, RDatasets, StatsModels

# データセットを取得
mtcars = dataset("datasets", "mtcars")

# モデルを訓練
container = fit(@formula(MPG ~ HP + WT + Gear), mtcars, LinearRegression())

# adjr2 を取得
adjr2(container)
```
