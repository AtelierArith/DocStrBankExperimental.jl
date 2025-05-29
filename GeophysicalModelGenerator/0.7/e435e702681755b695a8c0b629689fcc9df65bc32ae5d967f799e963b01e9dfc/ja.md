```
ParaviewData(x::GeoUnit, y::GeoUnit, z::GeoUnit, values::NamedTuple)
```

Paraviewで使用するための`x/y/z`座標の直交データ。これは通常、`GeoData`構造体から自動的に生成されますが、手動でこれを呼び出すこともできます：

```julia-repl
julia> Data_set    =   GeophysicalModelGenerator.GeoData(1.0:10.0,11.0:20.0,(-20:-11)*km,(DataFieldName=(-20:-11),))
julia> Data_cart = convert(ParaviewData, Data_set)
```
