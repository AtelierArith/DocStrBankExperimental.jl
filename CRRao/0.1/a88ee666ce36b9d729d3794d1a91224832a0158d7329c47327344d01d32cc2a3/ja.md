```julia
aic(container::FrequentistRegression)
```

赤池情報量基準。`aic` メソッドを [StatsAPI.jl](https://github.com/JuliaStats/StatsAPI.jl) から拡張します。

# 例

```julia
using CRRao, RDatasets, StatsModels

# データセットを取得
mtcars = dataset("datasets", "mtcars")

# モデルを訓練
container = fit(@formula(MPG ~ HP + WT + Gear), mtcars, LinearRegression())

# aic を取得
aic(container)
```
