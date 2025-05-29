```
ERA5Region(
    ID :: AbstractString;
    resolution :: Real = 0,
    ST = String,
    FT = Float64
) -> ereg :: ERA5Region
```

# 引数

  * `ID` : `GeoRegion`を指定するために使用されるID

# キーワード引数

  * `resolution` : ERA5再解析データがダウンロード/分析される空間解像度であり、360は`resolution`の倍数でなければなりません
