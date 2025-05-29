```
function get_β(Sₐ::Raster, Θ::Raster, p::Raster)
function get_β(stack::RasterStack, var_names::NamedTuple)
function get_β(series::RasterSeries, var_names::NamedTuple)
```

ハリネコ収縮係数 `β` を、GibbsSeaWater.jl の `gsw_beta` を使用して計算します。`RasterStack` または `RasterSeries` から `β` を計算するには、変数名を `(Sₐ = :salt_var, Θ = :temp_var, p = :pressure_var)` の形式で `NamedTuple` として関数に渡す必要があります。返される `Raster` は、渡された `Rasterstack` と同じ次元を持ちます。
