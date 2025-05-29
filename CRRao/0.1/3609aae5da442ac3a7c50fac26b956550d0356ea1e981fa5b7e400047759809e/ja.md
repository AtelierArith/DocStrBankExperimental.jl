```julia
r2(container::FrequentistRegression)
```

決定係数。`r2` メソッドを [StatsAPI.jl](https://github.com/JuliaStats/StatsAPI.jl) から拡張します。

# 例

```julia
using CRRao, RDatasets, StatsModels

# データセットを取得
mtcars = dataset("datasets", "mtcars")

# モデルを訓練
container = fit(@formula(MPG ~ HP + WT + Gear), mtcars, LinearRegression())

# r2を取得
r2(container)
```
