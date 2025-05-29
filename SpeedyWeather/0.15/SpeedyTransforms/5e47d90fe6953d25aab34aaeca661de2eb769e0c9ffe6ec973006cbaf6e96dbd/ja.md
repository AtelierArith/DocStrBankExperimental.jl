```julia
transform(
    grids::SpeedyWeather.RingGrids.AbstractGridArray,
    S::SpeedyWeather.SpeedyTransforms.SpectralTransform{NF}
) -> Any

```

`grids` から新しく割り当てられた `specs::LowerTriangularArray` への球面調和変換で、事前に計算されたスペクトル変換 `S` を使用します。
