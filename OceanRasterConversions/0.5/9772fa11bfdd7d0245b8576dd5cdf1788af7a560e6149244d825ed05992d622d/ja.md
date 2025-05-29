```
function get_σₚ(Sₐ::Raster, Θ::Raster, p::Number)
function get_σₚ(stack::RasterStack, var_names::NamedTuple)
function get_σₚ(series::RasterStack, var_names::NamedTuple)
```

参照圧力 `p` での潜在密度 `σₚ` を、GibbsSeaWater.jl の `gsw_rho` を使用して計算します。この計算は、絶対塩分 (`Sₐ`)、保守温度 (`Θ`)、およびユーザーが入力した参照圧力 (`p`) に依存します。`RasterStack` または `RasterSeries` から参照圧力 `p` での潜在密度 `σₚ` を計算して返します。この計算は、絶対塩分 `Sₐ`、保守温度 `Θ`、および参照圧力 `p` に依存します。変数名は、`(Sₐ = :salt_var, Θ = :temp_var, p = ref_pressure)` の形式で `NamedTuple` として関数に渡す必要があります。この場合の `p` は数値です。返される `Raster` は、渡された `Rasterstack` と同じ次元を持ちます。
