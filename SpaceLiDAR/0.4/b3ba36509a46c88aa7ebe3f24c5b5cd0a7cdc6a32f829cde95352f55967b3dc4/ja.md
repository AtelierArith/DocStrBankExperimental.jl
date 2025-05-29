```
points(g::ICESat_Granule{:GLAH06}, step=1, bbox::Union{Nothing,Extent,NamedTuple} = nothing)
```

ICESat GLAH06（陸氷）グラニュールのポイントを名前付きタプルのリストとして取得します。タプルの名前は以下のフィールドに基づいています：

| 変数                 | 元のフィールド                               | 説明                                                    | 単位          |
|:------------------ |:------------------------------------- |:----------------------------------------------------- |:----------- |
| `longitude`        | `Data_40HZ/Geolocation/d_lon`         | セグメント中心の経度、WGS84、東=+                                  | 小数度         |
| `latitude`         | `Data_40HZ/Geolocation/d_lat`         | セグメント中心の緯度、WGS84、北=+                                  | 小数度         |
| `height`           | `Data_40HZ/Elevation_Surfaces/d_elev` | + `Data_40HZ/Elevation_Corrections/d_satElevCorr`     | WGS84楕円体上のm |
| `datetime`         | `Data_40HZ/DS_UTCTime_40`             | 取得の正確な時間                                              | 日時          |
| `quality` [^1]     | `Data_40HZ/Quality/elev_use_flg`      | & `Data_40HZ/Quality/sigma_att_flg` = 0               |             |
|                    | & `Data_40HZ/Waveform/i_numPk` = 1    | & `Data_40HZ/Elevation_Corrections/d_satElevCorr` < 3 | 1 = 高品質     |
| `height_reference` | `land_ice_segments/dem/dem_h`         | （利用可能な最良の）DEMの高さ                                      | WGS84上の高さ   |

出力は `DataFrame(points(g))` で `DataFrame` 形式で取得できます。

[^1]: Smith, B., Fricker, H. A., Gardner, A. S., Medley, B., Nilsson, J., Paolo, F. S., ... & Zwally, H. J. (2020). Pervasive ice sheet mass loss reflects competing ocean and atmosphere processes. Science, 368(6496), 1239-1242.
