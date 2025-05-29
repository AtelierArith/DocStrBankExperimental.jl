```
function get_α(Sₐ::Raster, Θ::Raster, p::Raster)
function get_α(stack::RasterStack, var_names::NamedTuple)
function get_α(series::RasterSeries, var_names::NamedTuple)
```

熱膨張係数 `α` を、GibbsSeaWater.jl の `gsw_alpha` を使用して計算します。`RasterStack` または `RasterSeries` から `α` を計算するには、変数名を `(Sₐ = :salt_var, Θ = :temp_var, p = :pressure_var)` の形式で `NamedTuple` として関数に渡す必要があります。返される `Raster` は、渡された `Rasterstack` と同じ次元を持ちます。
