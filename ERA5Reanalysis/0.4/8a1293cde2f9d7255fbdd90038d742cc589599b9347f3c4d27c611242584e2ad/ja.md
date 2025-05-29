```
ERA5Region(
    geo :: GeoRegion;
    resolution :: Real = 0,
    ST = String,
    FT = Float64
) -> ereg :: ERA5Region
```

# 引数

  * `geo`  : `GeoRegion` 構造体タイプ

# キーワード引数

  * `resolution` : ERA5 再解析データがダウンロード/分析される空間解像度であり、360 は `resolution` の倍数でなければなりません。
