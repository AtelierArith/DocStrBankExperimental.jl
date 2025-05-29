```julia
coeftable(container::FrequentistRegression)
```

モデルの係数とその他の統計の表。`coeftable` メソッドを [StatsAPI.jl](https://github.com/JuliaStats/StatsAPI.jl) から拡張します。

# 例

```julia
using CRRao, RDatasets, StatsModels

# データセットを取得
mtcars = dataset("datasets", "mtcars")

# モデルを訓練
container = fit(@formula(MPG ~ HP + WT + Gear), mtcars, LinearRegression())

# 係数の表を取得
coeftable(container)
```
