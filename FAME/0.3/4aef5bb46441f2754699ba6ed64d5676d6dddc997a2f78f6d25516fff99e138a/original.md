```
refame(name, value)
```

Convert the given value to a [`FameObject`](@ref)

  * `Real` => NUMERIC SCALAR (includes integers)
  * `Float64` => PRECISION SCALAR
  * `Bool` => BOOLEAN SCALAR
  * [`MIT`](@ref TimeSeriesEcon.MIT) => DATE SCALAR
  * `String` => NAMELIST, if it is in the form "{name1,name2,...}", otherwise STRING SCALAR
  * `Vector{String}` => CASE SERIES of STRING
  * [`TSeries`](@ref TimeSeriesEcon.TSeries) => a SERIES of the same frequency and type. The type conversions are the same as for scalars.
