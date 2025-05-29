```
Data = screenshot_to_UTMData(filename::String, Corner_LowerLeft, Corner_UpperRight; Corner_LowerRight=nothing, Corner_UpperLeft=nothing, UTMzone::Int64=nothing, isnorth::Bool=true, fieldname=:colors)
```

`screenshot_to_GeoData`と同じことをしますが、UTMデータを返します。`UTMzone`と`isnorth`を指定する必要があることに注意してください。
