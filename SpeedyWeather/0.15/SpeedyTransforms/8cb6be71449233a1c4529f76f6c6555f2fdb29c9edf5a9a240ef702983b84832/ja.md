```julia
SpectralTransform(
    specs::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray{NF, N, ArrayType};
    nlat_half,
    dealiasing,
    kwargs...
) -> SpeedyWeather.SpeedyTransforms.SpectralTransform{NF, _A, _B, _C, _D, _E, SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray{NF1, 1, _A1}, SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray{NF2, 2, _A2}} where {NF, _A, _B, _C, _D, _E, NF1, _A1, NF2, _A2}

```

`SpectralTransform` 構造体の生成関数で、スペクトル係数 `specs` のサイズに基づいています。キーワード引数 `nlat_half`、`Grid` または `deliasing`（`nlat_half` が提供されていない場合）を使用してグリッドを定義します。
