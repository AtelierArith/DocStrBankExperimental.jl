```
unfame(fo::FameObject)
```

Convert a `FameObject` to a Julia type.

  * PRECISION SCALAR => `Float64`
  * NUMERIC SCALAR => `Float32`
  * STRING SCALAR => `String`
  * BOOLEAN SCALAR => `Bool`
  * NAMELIST => `String` (Formatted as "{NAME1,NAME2,ETC}", see Fame help for details.)
  * DATE SCALAR => [`MIT`](@ref TimeSeriesEcon.MIT) (CASE becomes `MIT{Unit}`, Frequencies not supported by TimeSeriesEcon throw an `ErrorException`)
  * PRECISION SERIES => [`TSeries`](@ref TimeSeriesEcon.TSeries)
  * NUMERIC SERIES => [`TSeries`](@ref TimeSeriesEcon.TSeries) with element type `Float32`
  * BOOLEAN SERIES => [`TSeries`](@ref TimeSeriesEcon.TSeries) with element type `Bool`
  * DATE SERIES => [`TSeries`](@ref TimeSeriesEcon.TSeries) with element type [`MIT`](@ref TimeSeriesEcon.MIT)
  * STRING SERIES => `Vector{String}` (the time series metadata is lost)
