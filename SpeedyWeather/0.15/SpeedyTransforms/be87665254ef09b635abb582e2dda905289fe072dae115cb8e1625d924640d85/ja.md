```julia
SpectralTransform(
    grids::SpeedyWeather.RingGrids.AbstractGridArray{NF, N, ArrayType};
    trunc,
    dealiasing,
    one_more_degree,
    kwargs...
) -> SpeedyWeather.SpeedyTransforms.SpectralTransform{NF, _A, _B, _C, _D, _E, SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray{NF1, 1, _A1}, SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray{NF2, 2, _A2}} where {NF, _A, _B, _C, _D, _E, NF1, _A1, NF2, _A2}

```

`SpectralTransform` 構造体の生成関数で、`grids` のサイズとグリッドタイプに基づいています。キーワード引数 `trunc`、`dealiasing`（`trunc` が使用されている場合は無視されます）または `one_more_degree` を使用してスペクトルの切り捨てを定義します。
