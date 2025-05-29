```
initialize_surfacevelocitydata(
    raster::Union{String, RasterStack};
    glacier::Union{G, Nothing}=nothing,
    mapping::VM=MeanDateVelocityMapping(),
    compute_vabs_error::Bool=true
) where {G <: AbstractGlacier, VM <: VelocityMapping}
```

Rabatel et al. (2023) に基づいて SurfaceVelocityData を初期化します。

引数:

  * `raster::Union{String, RasterStack}`: サーフェス速度データを含む RasterStack または netCDF ファイルのパス。
  * `glacier::Union{G, Nothing}`: サーフェス速度データキューブに関連付けられた氷河。提供された場合、サーフェス速度データは `mapping` を使用して氷河グリッド上にグリッド化されます。
  * `mapping::VM`: サーフェス速度データキューブの座標から氷河グリッドへのデータをグリッド化するために使用するマッピング。
  * `compute_vabs_error::Bool`: 絶対誤差の不確実性を計算するかどうか。
