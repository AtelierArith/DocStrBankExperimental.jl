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

Constructor for NetCDFOutput based on `S::SpectralGrid` and optionally the `Model` type (e.g. `ShallowWater`, `PrimitiveWet`) as second positional argument. The output grid is optionally determined by keyword arguments `output_Grid` (its type, full grid required), `nlat_half` (resolution) and `output_NF` (number format). By default, uses the full grid equivalent of the grid and resolution used in `SpectralGrid` `S`.
