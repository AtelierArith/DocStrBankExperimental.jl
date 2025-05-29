```julia
bic(container::FrequentistRegression)
```

ベイズ情報基準。`bic`メソッドを[StatsAPI.jl](https://github.com/JuliaStats/StatsAPI.jl)から拡張します。

# 例

```julia
using CRRao, RDatasets, StatsModels

# データセットを取得
mtcars = dataset("datasets", "mtcars")

# モデルを訓練
container = fit(@formula(MPG ~ HP + WT + Gear), mtcars, LinearRegression())

# bicを取得
bic(container)
```
