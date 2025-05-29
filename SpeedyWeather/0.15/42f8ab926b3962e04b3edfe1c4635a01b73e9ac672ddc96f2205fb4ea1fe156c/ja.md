```julia
initialize!(
    land_sea_mask::SpeedyWeather.EarthLandSeaMask,
    model::SpeedyWeather.PrimitiveEquation
) -> AbstractArray

```

ファイルから高解像度の陸海マスクを読み込み、モデルグリッドに補間（グリッドセル平均）して、部分的な海マスクを作成します。
