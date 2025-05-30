```
points(g::ICESat2_Granule{:ATL12}, tracks=icesat2_tracks)
```

与えられた ICESat-2 ATL12 (海面高さ) グラニュールのポイントを、ビームごとに1つの名前付きタプルのリストとして取得します。タプルの名前は以下のフィールドに基づいています：

| 列             | フィールド                     | 説明                                                    | 単位             |
|:------------- |:------------------------- |:----------------------------------------------------- |:-------------- |
| `longitude`   | `ssh_segments/longitude`  | セグメント中心の経度、WGS84、東=+                                  | 小数度            |
| `latitude`    | `ssh_segments/latitude`   | セグメント中心の緯度、WGS84、北=+                                  | 小数度            |
| `height`      | `ssh_segments/heights/h`  | 標準的な陸氷セグメントの高さ                                        | WGS 84 楕円体上の m |
| `datetime`    | `ssh_segments/delta_time` | + `ancillary_data/atlas_sdp_gps_epoch` + `gps_offset` | 日時             |
| `track`       | `gt1l` - `gt3r` グループ      | -                                                     | -              |
| `strong_beam` | `-`                       | "強い" (true) または "弱い" (false) レーザーパワー                  | -              |
| `detector_id` | `atlas_spot_number 属性`    | -                                                     | -              |

出力を `DataFrame` に結合するには、デフォルトの引数を変更したい場合は `reduce(vcat, DataFrame.(points(g)))` を使用するか、デフォルトオプションで `DataFrame(g)` を使用します。
