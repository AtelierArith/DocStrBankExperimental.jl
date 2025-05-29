```
lonlat2bng(lon, lat) -> easting, northing
```

WGS84の経度`lon`と緯度`lat`（度）をBNGの`easting`と`northing`（m）に変換します。

!!! note
    この関数は、`lon`と`lat`が国土グリッドの範囲外の点にある場合にエラーをスローしません。したがって、この関数は注意して使用する必要があります。


# 例

```jldoctest
julia> lon, lat = -3.183503, 55.954983;

julia> lonlat2bng(lon, lat)
(326200.06052230217, 674183.9198954724)

```
