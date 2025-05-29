```
XYZ21{T1 <: Signed, T2 <: AbstractFloat} <: XYZ{T1, T2}
```

2021 SGLデータセットの`XYZ`のサブタイプ。

| **フィールド**   | **型**           | **説明**                            |
|:----------- |:--------------- |:--------------------------------- |
| `info`      | String          | データセット情報                          |
| `traj`      | Traj{`T1`,`T2`} | 軌道構造体                             |
| `ins`       | INS{`T1`,`T2`}  | 慣性航法システム構造体                       |
| `flux_a`    | MagV{`T2`}      | フラックスAベクトル磁力計測定構造体                |
| `flux_b`    | MagV{`T2`}      | フラックスBベクトル磁力計測定構造体                |
| `flux_c`    | MagV{`T2`}      | フラックスCベクトル磁力計測定構造体                |
| `flux_d`    | MagV{`T2`}      | フラックスDベクトル磁力計測定構造体                |
| `flight`    | Vector{`T2`}    | フライト番号                            |
| `line`      | Vector{`T2`}    | ライン番号、すなわち`flight`内のセグメント         |
| `year`      | Vector{`T2`}    | 年                                 |
| `doy`       | Vector{`T2`}    | 年の日                               |
| `utm_x`     | Vector{`T2`}    | x座標、WGS-84 UTMゾーン18N [m]          |
| `utm_y`     | Vector{`T2`}    | y座標、WGS-84 UTMゾーン18N [m]          |
| `utm_z`     | Vector{`T2`}    | z座標、WGS-84楕円体上のGPS高度 [m]          |
| `msl`       | Vector{`T2`}    | z座標、EGM2008ジオイド上のGPS高度 [m]        |
| `baro`      | Vector{`T2`}    | 気圧高度計 [m]                         |
| `diurnal`   | Vector{`T2`}    | 測定された日変化、すなわち時間的変動または宇宙天気の影響 [nT] |
| `igrf`      | Vector{`T2`}    | 国際地磁気基準場（IGRF）、すなわちコアフィールド [nT]   |
| `mag_1_c`   | Vector{`T2`}    | Mag 1補正済み（クリーン）スカラー磁力計測定 [nT]     |
| `mag_1_uc`  | Vector{`T2`}    | Mag 1非補正（破損）スカラー磁力計測定 [nT]        |
| `mag_2_uc`  | Vector{`T2`}    | Mag 2非補正（破損）スカラー磁力計測定 [nT]        |
| `mag_3_uc`  | Vector{`T2`}    | Mag 3非補正（破損）スカラー磁力計測定 [nT]        |
| `mag_4_uc`  | Vector{`T2`}    | Mag 4非補正（破損）スカラー磁力計測定 [nT]        |
| `mag_5_uc`  | Vector{`T2`}    | Mag 5非補正（破損）スカラー磁力計測定 [nT]        |
| `cur_com_1` | Vector{`T2`}    | 電流センサー：航空機ラジオ1 [A]                |
| `cur_ac_hi` | Vector{`T2`}    | 電流センサー：エアコンファン高 [A]               |
| `cur_ac_lo` | Vector{`T2`}    | 電流センサー：エアコンファン低 [A]               |
| `cur_tank`  | Vector{`T2`}    | 電流センサー：キャビン燃料ポンプ [A]              |
| `cur_flap`  | Vector{`T2`}    | 電流センサー：フラップモーター [A]               |
| `cur_strb`  | Vector{`T2`}    | 電流センサー：ストロボライト [A]                |
| `vol_block` | Vector{`T2`}    | 電圧センサー：ブロック [V]                   |
| `vol_back`  | Vector{`T2`}    | 電圧センサー：バックプレーン [V]                |
| `vol_cabt`  | Vector{`T2`}    | 電圧センサー：キャビネット [V]                 |
| `vol_fan`   | Vector{`T2`}    | 電圧センサー：冷却ファン [V]                  |
| `aux_1`     | Vector{`T2`}    | 柔軟使用の補助データ1                       |
| `aux_2`     | Vector{`T2`}    | 柔軟使用の補助データ2                       |
| `aux_3`     | Vector{`T2`}    | 柔軟使用の補助データ3                       |

```
