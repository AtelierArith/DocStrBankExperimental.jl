```
function θ_to_Θ(θ::Raster, Sₐ::Raster)
function θ_to_Θ(stack::RasterStack, var_names::NamedTuple)
function θ_to_Θ(series::RasterSeries, var_names::NamedTuple)
```

ポテンシャル温度（`θ`）の `Raster` を、GibbsSeaWater.jl の `gsw_ct_from_pt` を使用して保守的温度（`Θ`）に変換します。この変換は絶対塩分に依存します。`RasterStack` または `RasterSeries` から変換する場合、`var_names` は `convert_ocean_vars` のように渡す必要があります。すなわち、`(Sₚ = :salt_name, θ = :potential_temp_name)` の形式の名前付きタプルとして渡す必要があります。ここで、`:potential_temp_name` と `:salt_name` は `RasterStack` 内のポテンシャル温度と塩分の名前です。
