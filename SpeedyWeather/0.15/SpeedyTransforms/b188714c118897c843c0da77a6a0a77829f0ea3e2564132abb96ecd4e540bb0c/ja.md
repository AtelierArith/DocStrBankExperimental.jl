```julia
transform(
    specs::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    S::SpeedyWeather.SpeedyTransforms.SpectralTransform{NF};
    kwargs...
) -> Any

```

`specs`から新しく割り当てられた`grids::AbstractGridArray`への球面調和変換で、事前に計算されたスペクトル変換`S`を使用します。
