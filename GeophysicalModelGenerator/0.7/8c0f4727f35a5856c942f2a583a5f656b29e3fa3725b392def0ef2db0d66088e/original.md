```
Data = screenshot_to_UTMData(filename::String, Corner_LowerLeft, Corner_UpperRight; Corner_LowerRight=nothing, Corner_UpperLeft=nothing, UTMzone::Int64=nothing, isnorth::Bool=true, fieldname=:colors)
```

Does the same as `screenshot_to_GeoData`, but returns for UTM data Note that you have to specify the `UTMzone` and `isnorth`
