```julia
residuals(container::FrequentistRegression)
```

モデルの残差。`[StatsAPI.jl](https://github.com/JuliaStats/StatsAPI.jl)`から`residuals`メソッドを拡張します。

# 例

```julia
using CRRao, RDatasets, StatsModels

# データセットを取得
mtcars = dataset("datasets", "mtcars")

# モデルを訓練
container = fit(@formula(MPG ~ HP + WT + Gear), mtcars, LinearRegression())

# 残差を取得
residuals(container)
```
