```julia
power_spectrum(
    spec::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray;
    normalize
) -> Any

```

球面調和係数 `spec`（下三角行列/配列）のパワースペクトルを計算します。`spec` の型は `Complex{NF}` です。`spec` に追加の次元がある場合、パワースペクトルは最初の/球面調和次元に沿って計算されます。
