```julia
eachharmonic(
    L::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray
) -> Any

```

は、LowerTriangularArray `L` のすべての非ゼロ/球面調和数をループするために `unit_range::UnitRange` を作成します。`eachindex` のようですが、`L` の上三角のゼロをスキップします。
