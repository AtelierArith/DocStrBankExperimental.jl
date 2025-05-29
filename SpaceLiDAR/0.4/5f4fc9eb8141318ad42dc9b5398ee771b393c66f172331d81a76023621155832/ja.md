```
points(g::ICESat2_Granule{:ATL03}, tracks=icesat2_tracks; step=1, bbox::Union{Nothing,Extent,NamedTuple} = nothing)
```

与えられた ICESat-2 ATL03 (グローバルジオロケートフォトンデータ) グラニュールのポイントを、ビームごとに1つの名前付きタプルのリストとして取得します。タプルの名前は以下のフィールドに基づいています：

| 列                  | フィールド                         | 説明                                                    | 単位            |
|:------------------ |:----------------------------- |:----------------------------------------------------- |:------------- |
| `longitude`        | `heights/lon_ph`              | フォトンの経度、WGS84、東=+                                     | 小数度           |
| `latitude`         | `heights/lat_ph`              | フォトンの緯度、WGS84、北=+                                     | 小数度           |
| `height`           | `heights/h_ph`                | フォトンのWGS84高さ                                          | WGS 84楕円体上のm  |
| `quality`          | `heights/quality_ph`          | 関連するフォトンの品質を示す                                        | 0 = 標準        |
| `uncertainty`      | `geolocation/sigma_h`         | 推定された高さの不確実性                                          | m             |
| `datetime`         | `heights/delta_time`          | + `ancillary_data/atlas_sdp_gps_epoch` + `gps_offset` | 日時            |
| `confidence`       | `heights/signal_conf_ph`      | フォトン信号の信頼性                                            | 2=低; 3=中; 4=高 |
| `segment`          | `geolocation/segment_id`      | トラックに沿ったセグメントID番号                                     | -             |
| `track`            | `gt1l` - `gt3r` グループ          | -                                                     | -             |
| `strong_beam`      | `-`                           | "強い" (true) または "弱い" (false) レーザーパワー                  | -             |
| `sun_angle`        | `geolocation/solar_elevation` | 太陽角                                                   | 地平線上の°        |
| `detector_id`      | `atlas_spot_number attribute` | -                                                     | -             |
| `height_reference` | `heights/dem/dem_h`           | (利用可能な最良の) DEMの高さ                                     | WGS 84楕円体上のm  |

デフォルトの引数を変更したい場合は、`reduce(vcat, DataFrame.(points(g)))`で出力を`DataFrame`に結合できます。または、デフォルトオプションで`DataFrame(g)`を使用できます。
