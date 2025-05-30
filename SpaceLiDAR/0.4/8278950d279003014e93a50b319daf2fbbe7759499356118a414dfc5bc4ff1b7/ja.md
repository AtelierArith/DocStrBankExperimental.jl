```
points(g::ICESat2_Granule{:ATL06}, tracks=icesat2_tracks, step=1, bbox::Union{Nothing,Extent,NamedTuple} = nothing)
```

与えられた ICESat-2 ATL06 (Land Ice) グラニュールのポイントを、ビームごとに1つの名前付きタプルのリストとして取得します。タプルの名前は以下のフィールドに基づいています：

| 列                  | フィールド                                     | 説明                                                    | 単位             |
|:------------------ |:----------------------------------------- |:----------------------------------------------------- |:-------------- |
| `longitude`        | `land_ice_segments/longitude`             | セグメント中心の経度、WGS84、東=+                                  | 小数度            |
| `latitude`         | `land_ice_segments/latitude`              | セグメント中心の緯度、WGS84、北=+                                  | 小数度            |
| `height`           | `land_ice_segments/h_li`                  | 標準的な陸氷セグメントの高さ                                        | WGS 84 楕円体上の m |
| `height_error`     | √(`land_ice_segments/sigma_geo_h`² +      | 総垂直位置決定誤差                                             | WGS 84 楕円体上の m |
|                    | `land_ice_segments/h_li_sigma`²)          |                                                       |                |
| `datetime`         | `land_ice_segments/delta_time`            | + `ancillary_data/atlas_sdp_gps_epoch` + `gps_offset` | 日時             |
| `quality`          | `land_ice_segments/atl06_quality_summary` | 最良の品質サブセットを示すブールフラグ                                   | 1 = 高品質        |
| `track`            | `gt1l` - `gt3r` グループ                      | -                                                     | -              |
| `strong_beam`      | `-`                                       | "強い" (true) または "弱い" (false) レーザーパワー                  | -              |
| `detector_id`      | `atlas_spot_number attribute`             | -                                                     | -              |
| `height_reference` | `land_ice_segments/dem/dem_h`             | (利用可能な中で最良の) DEM の高さ                                  | -              |

デフォルトの引数を変更したい場合は、`reduce(vcat, DataFrame.(points(g)))` で出力を `DataFrame` に結合できます。または、デフォルトオプションで `DataFrame(g)` を使用できます。
