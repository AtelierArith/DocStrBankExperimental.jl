```
ParaviewData(x::GeoUnit, y::GeoUnit, z::GeoUnit, values::NamedTuple)
```

Cartesian data in `x/y/z` coordinates to be used with Paraview. This is usually generated automatically from the `GeoData` structure, but you can also invoke do this manually:

```julia-repl
julia> Data_set    =   GeophysicalModelGenerator.GeoData(1.0:10.0,11.0:20.0,(-20:-11)*km,(DataFieldName=(-20:-11),))
julia> Data_cart = convert(ParaviewData, Data_set)
```
