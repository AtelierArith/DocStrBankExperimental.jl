```julia
sigma(container::FrequentistRegression)
```

`σ`は[StatsAPI.jl](https://github.com/JuliaStats/StatsAPI.jl)から残差標準誤差を計算します。

# 例

```julia
using CRRao, RDatasets, StatsModels

# データセットを取得
mtcars = dataset("datasets", "mtcars")

# モデルを訓練
container = fit(@formula(MPG ~ HP + WT + Gear), mtcars, LinearRegression())

# σを取得
sigma(container)
```
