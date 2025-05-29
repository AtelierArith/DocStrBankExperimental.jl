```julia
loglikelihood(container::FrequentistRegression)
```

モデルの対数尤度。`loglikelihood` メソッドを [StatsAPI.jl](https://github.com/JuliaStats/StatsAPI.jl) から拡張します。

# 例

```julia
using CRRao, RDatasets, StatsModels

# データセットを取得
mtcars = dataset("datasets", "mtcars")

# モデルを訓練
container = fit(@formula(MPG ~ HP + WT + Gear), mtcars, LinearRegression())

# 対数尤度を取得
adjr2(container)
```
