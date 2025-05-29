```
function Sₚ_to_Sₐ(Sₚ::Raster)
function Sₚ_to_Sₐ(stack::RasterStack, Sₚ::Symbol)
function Sₚ_to_Sₐ(series::RasterSeries, Sₚ::Symbol)
```

実用塩分（`Sₚ`）の `Raster` を絶対塩分（`Sₐ`）に変換するには、GibbsSeaWater.jl の `gsw_sa_from_sp` を使用します。この変換は圧力に依存します。`RasterStack` または `RasterSeries` から変換する場合、`RasterStack/Series` 内の実用塩分のシンボルを `Symbol` として渡す必要があります。つまり、変数名が SALT の場合、`RasterStack/Series` に対して `Symbol` `:SALT` を渡す必要があります。
