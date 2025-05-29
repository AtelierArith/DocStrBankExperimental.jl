```
points(g::ICESat_Granule{:GLAH14}, step=1, bbox::Union{Nothing,Extent,NamedTuple} = nothing)
```

与えられた ICESat GLAH14 (陸面) グラニュールのポイントを名前付きタプルのリストとして取得します。タプルの名前は以下のフィールドに基づいています：

| 変数                 | 元のフィールド (`Data_40HZ` 内)         | 説明                                          | 単位                   |
|:------------------ |:------------------------------- |:------------------------------------------- |:-------------------- |
| `longitude`        | `/Geolocation/d_lon`            | セグメント中心の経度、WGS84、東=+                        | 小数度                  |
| `latitude`         | `Geolocation/d_lat`             | セグメント中心の緯度、WGS84、北=+                        | 小数度                  |
| `height`           | `Elevation_Surfaces/d_elev`     | + `Elevation_Corrections/d_satElevCorr`     | WGS84 楕円体上の m        |
| `datetime`         | `DS_UTCTime_40`                 | 取得の正確な時間                                    | 日時                   |
| `quality` [^1]     | `Quality/elev_use_flg`          | & `Quality/sigma_att_flg` = 0               |                      |
|                    | & `Waveform/i_numPk` = 1        | & `Elevation_Corrections/d_satElevCorr` < 3 | 1=高品質                |
| `clouds`           | `Elevation_Flags/elv_cloud_flg` | 雲の汚染                                        | -                    |
| `height_reference` | `Geophysical/d_DEM_elv`         | (利用可能な) DEM の高さ                             | WGS84 上の高さ           |
| `gain`             | `Waveform/i_gval_rcv`           | 受信パルスに使用されるゲイン値。                            | -                    |
| `reflectivity`     | `Reflectivity/d_reflctUC`       | 修正されていない反射率                                 | -                    |
| `attitude`         | `Quality/sigma_att_flg`         | 姿勢の品質指標                                     | 0=良好; 50=警告; 100=悪い; |
| `saturation`       | `Quality/sat_corr_flg`          | 飽和補正フラグ                                     | 0=飽和していない;           |

`DataFrame(points(g))` を使用して出力を `DataFrame` で取得できます。

[^1]: Smith, B., Fricker, H. A., Gardner, A. S., Medley, B., Nilsson, J., Paolo, F. S., ... & Zwally, H. J. (2020). Pervasive ice sheet mass loss reflects competing ocean and atmosphere processes. Science, 368(6496), 1239-1242.
