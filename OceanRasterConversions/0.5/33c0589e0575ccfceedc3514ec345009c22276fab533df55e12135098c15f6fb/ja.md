```
function get_ρ(Sₐ::Raster, Θ::Raster, p::Raster)
function get_ρ(stack::RasterStack, var_names::NamedTuple)
function get_ρ(series::RasterStack, var_names::NamedTuple)
```

`gsw_rho`を使用して、現場密度`ρ`を計算します。これは、絶対塩分（`Sₐ`）、保存温度（`Θ`）、および圧力（`p`）に依存します。`RasterStack`または`RasterSeries`からρを計算するには、変数名を`NamedTuple`の形で関数に渡す必要があります（形式は`(Sₐ = :salt_var, Θ = :temp_var, p = :pressure_var)`）。返される`Raster`は、渡された`Rasterstack`と同じ次元を持ちます。
