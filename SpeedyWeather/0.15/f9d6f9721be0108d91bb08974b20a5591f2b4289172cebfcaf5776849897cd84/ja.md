```julia
NetCDFOutput(
    S::SpeedyWeather.SpectralGrid;
    ...
) -> SpeedyWeather.NetCDFOutput{_A, _B, Interpolator} where {_A, _B, Interpolator<:(SpeedyWeather.RingGrids.AnvilInterpolator{Float32, _A, SpeedyWeather.RingGrids.GridGeometry{Grid, VectorType, VectorIntType, VectorRangeType}, SpeedyWeather.RingGrids.AnvilLocator{Float32, _A1, _B}} where {_A, Grid, VectorType, VectorIntType, VectorRangeType, _A1, _B})}
NetCDFOutput(
    S::SpeedyWeather.SpectralGrid,
    Model::Type{<:SpeedyWeather.AbstractModel};
    output_Grid,
    nlat_half,
    output_NF,
    output_dt,
    kwargs...
) -> SpeedyWeather.NetCDFOutput{_A, _B, Interpolator} where {_A, _B, Interpolator<:(SpeedyWeather.RingGrids.AnvilInterpolator{Float32, _A, SpeedyWeather.RingGrids.GridGeometry{Grid, VectorType, VectorIntType, VectorRangeType}, SpeedyWeather.RingGrids.AnvilLocator{Float32, _A1, _B}} where {_A, Grid, VectorType, VectorIntType, VectorRangeType, _A1, _B})}

```

`S::SpectralGrid`に基づくNetCDFOutputのコンストラクタで、オプションで`Model`型（例：`ShallowWater`、`PrimitiveWet`）を第二の位置引数として指定できます。出力グリッドは、キーワード引数`output_Grid`（その型、完全なグリッドが必要）、`nlat_half`（解像度）、および`output_NF`（数値形式）によってオプションで決定されます。デフォルトでは、`SpectralGrid` `S`で使用されるグリッドと解像度の完全なグリッドに相当するものが使用されます。
