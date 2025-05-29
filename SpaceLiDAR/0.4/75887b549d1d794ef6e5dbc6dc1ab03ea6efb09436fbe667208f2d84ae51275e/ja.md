```
points(g::ICESat2_Granule{:ATL08}; tracks=icesat2_tracks, step=1, canopy=false, ground=true, bbox::Union{Nothing,Extent,NamedTuple} = nothing)
```

ICESat-2 ATL08（陸地および植生の高さ）グラニュールのポイントを、ビームごとに1つの名前付きタプルのリストとして取得します。`tracks`キーワードを使用して、含めるトラックを指定できます。デフォルトではすべてのトラックが含まれます。`step`キーワードを使用すると、ポイントの数を制限できます。デフォルトは1（すべてのポイント）です。`ground`および/または`canopy`を設定することで、地面および/またはキャノピーポイントを含めるかどうかを制御できます。最後に、`ground_field`および`canopy_field`の設定を使用して、ソースフィールドを決定できます。デフォルトは、地面に対して`h_te_mean`、キャノピーに対して`h_mean_canopy_abs`です。v5の導入により、20mの解像度での推定も可能になり、`highres`を使用して有効にできます。`highres`がtrueのとき、バウンディングボックスでのフィルタリングはまだ機能しないことに注意してください。

タプルの名前は、以下のフィールドに基づいています：

| 列                  | フィールド                                    | 説明                                                    | 単位           |
|:------------------ |:---------------------------------------- |:----------------------------------------------------- |:------------ |
| `longitude`        | `land_segments/longitude`                | セグメント中心の経度、WGS84、東=+                                  | 小数度          |
| `latitude`         | `land_segments/latitude`                 | セグメント中心の緯度、WGS84、北=+                                  | 小数度          |
| `height`           | `land_segments/terrain/h_te_mean`        | 標準的な陸氷セグメントの高さ                                        | WGS 84楕円体上のm |
| `height_error`     | `land_segments/terrain/h_te_uncertainty` | 総垂直位置決定誤差                                             | m            |
| `datetime`         | `land_segments/delta_time`               | + `ancillary_data/atlas_sdp_gps_epoch` + `gps_offset` | 日時           |
| `quality`          | `land_segments/terrain_flg`              | 最良品質のサブセットを示すブールフラグ                                   | 1 = 高品質      |
| `phr`              | `land_segments/ph_removal_flag`          | 50%以上のフォトンが除去された                                      | -            |
| `sensitivity`      | `land_segments/snr`                      | 信号対雑音比                                                | -            |
| `scattered`        | `land_segments/msw_flag`                 | 多重散乱警告フラグ                                             | -1=不明; 0=なし  |
| `saturated`        | `land_segments/sat_flag`                 | 飽和が検出された                                              | -            |
| `clouds`           | `land_segments/layer_flag`               | 雲または吹雪が存在する可能性が高い                                     | -            |
| `track`            | `gt1l` - `gt3r` グループ                     | -                                                     | -            |
| `strong_beam`      | `-`                                      | "強い"（true）または"弱い"（false）レーザーパワー                       | -            |
| `classification`   | `-`                                      | "地面"、"高いキャノピー"                                        | -            |
| `height_reference` | `land_segments/dem_h`                    | （利用可能な最良の）DEMの高さ                                      | WGS 84楕円体上のm |
| `detector_id`      | `atlas_spot_number attribute`            | -                                                     | -            |

デフォルトの引数を変更したい場合は、`reduce(vcat, DataFrame.(points(g)))`を使用して出力を`DataFrame`に結合できます。デフォルトオプションで`DataFrame(g)`を使用することもできます。
