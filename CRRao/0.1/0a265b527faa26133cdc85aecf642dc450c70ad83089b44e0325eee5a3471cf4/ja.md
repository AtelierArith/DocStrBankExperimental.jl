```julia
cooksdistance(container::FrequentistRegression)
```

線形モデルの各観測値に対するクックの距離を計算します。`cooksdistance`メソッドを[StatsAPI.jl](https://github.com/JuliaStats/StatsAPI.jl)から拡張しています。

# 例

```julia
using CRRao, RDatasets, StatsModels

# データセットを取得
mtcars = dataset("datasets", "mtcars")

# モデルを訓練
container = fit(@formula(MPG ~ HP + WT + Gear), mtcars, LinearRegression())

# クックの距離のベクトルを取得
cooksdistance(container)
```
