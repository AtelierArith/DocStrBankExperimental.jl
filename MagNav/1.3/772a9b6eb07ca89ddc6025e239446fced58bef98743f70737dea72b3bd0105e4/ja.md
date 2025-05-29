```
XYZ20{T1 <: Signed, T2 <: AbstractFloat} <: XYZ{T1, T2}
```

2020 SGLデータセット用の`XYZ`のサブタイプ。

| **フィールド**    | **型**           | **説明**                             |
|:------------ |:--------------- |:---------------------------------- |
| `info`       | String          | データセット情報                           |
| `traj`       | Traj{`T1`,`T2`} | 軌道構造体                              |
| `ins`        | INS{`T1`,`T2`}  | 慣性航法システム構造体                        |
| `flux_a`     | MagV{`T2`}      | フラックスAベクトル磁力計測定構造体                 |
| `flux_b`     | MagV{`T2`}      | フラックスBベクトル磁力計測定構造体                 |
| `flux_c`     | MagV{`T2`}      | フラックスCベクトル磁力計測定構造体                 |
| `flux_d`     | MagV{`T2`}      | フラックスDベクトル磁力計測定構造体                 |
| `flight`     | Vector{`T2`}    | フライト番号                             |
| `line`       | Vector{`T2`}    | ライン番号、すなわち`flight`内のセグメント          |
| `year`       | Vector{`T2`}    | 年                                  |
| `doy`        | Vector{`T2`}    | 年の日                                |
| `utm_x`      | Vector{`T2`}    | x座標、WGS-84 UTMゾーン18N [m]           |
| `utm_y`      | Vector{`T2`}    | y座標、WGS-84 UTMゾーン18N [m]           |
| `utm_z`      | Vector{`T2`}    | z座標、WGS-84楕円体上のGPS高度 [m]           |
| `msl`        | Vector{`T2`}    | z座標、EGM2008ジオイド上のGPS高度 [m]         |
| `baro`       | Vector{`T2`}    | 気圧高度計 [m]                          |
| `diurnal`    | Vector{`T2`}    | 測定された日変化、すなわち時間的変動または宇宙天気の影響 [nT]  |
| `igrf`       | Vector{`T2`}    | 国際地磁気基準場（IGRF）、すなわちコアフィールド [nT]    |
| `mag_1_c`    | Vector{`T2`}    | Mag 1補正済み（クリーン）スカラー磁力計測定 [nT]      |
| `mag_1_lag`  | Vector{`T2`}    | Mag 1遅延補正済みスカラー磁力計測定 [nT]          |
| `mag_1_dc`   | Vector{`T2`}    | Mag 1日変化補正済みスカラー磁力計測定 [nT]         |
| `mag_1_igrf` | Vector{`T2`}    | Mag 1 IGRF & 日変化補正済みスカラー磁力計測定 [nT] |
| `mag_1_uc`   | Vector{`T2`}    | Mag 1未補正（破損）スカラー磁力計測定 [nT]         |
| `mag_2_uc`   | Vector{`T2`}    | Mag 2未補正（破損）スカラー磁力計測定 [nT]         |
| `mag_3_uc`   | Vector{`T2`}    | Mag 3未補正（破損）スカラー磁力計測定 [nT]         |
| `mag_4_uc`   | Vector{`T2`}    | Mag 4未補正（破損）スカラー磁力計測定 [nT]         |
| `mag_5_uc`   | Vector{`T2`}    | Mag 5未補正（破損）スカラー磁力計測定 [nT]         |
| `mag_6_uc`   | Vector{`T2`}    | Mag 6未補正（破損）スカラー磁力計測定 [nT]         |
| `ogs_mag`    | Vector{`T2`}    | OGS調査日変化補正済み、レベル調整された磁場 [nT]       |
| `ogs_alt`    | Vector{`T2`}    | OGS調査、GPS高度（WGS-84） [m]            |
| `ins_wander` | Vector{`T2`}    | INS計算のワンダー角（北から反時計回り） [rad]        |
| `ins_roll`   | Vector{`T2`}    | INS計算の航空機ロール [deg]                 |
| `ins_pitch`  | Vector{`T2`}    | INS計算の航空機ピッチ [deg]                 |
| `ins_yaw`    | Vector{`T2`}    | INS計算の航空機ヨー [deg]                  |
| `roll_rate`  | Vector{`T2`}    | 航空電子機器計算のロールレート [deg/s]            |
| `pitch_rate` | Vector{`T2`}    | 航空電子機器計算のピッチレート [deg/s]            |
| `yaw_rate`   | Vector{`T2`}    | 航空電子機器計算のヨーレート [deg/s]             |
| `ins_acc_x`  | Vector{`T2`}    | INS x加速度 [m/s^2]                   |
| `ins_acc_y`  | Vector{`T2`}    | INS y加速度 [m/s^2]                   |
| `ins_acc_z`  | Vector{`T2`}    | INS z加速度 [m/s^2]                   |
| `lgtl_acc`   | Vector{`T2`}    | 航空電子機器計算の縦方向（前方）加速度 [g]            |
| `ltrl_acc`   | Vector{`T2`}    | 航空電子機器計算の横方向（右舷）加速度 [g]            |
| `nrml_acc`   | Vector{`T2`}    | 航空電子機器計算の法線（垂直）加速度 [g]             |
| `pitot_p`    | Vector{`T2`}    | 航空電子機器計算のピトー圧力 [kPa]               |
| `static_p`   | Vector{`T2`}    | 航空電子機器計算の静圧 [kPa]                  |
| `total_p`    | Vector{`T2`}    | 航空電子機器計算の総圧 [kPa]                  |
| `cur_com_1`  | Vector{`T2`}    | 電流センサー：航空機ラジオ1 [A]                 |
| `cur_ac_hi`  | Vector{`T2`}    | 電流センサー：エアコンファン高 [A]                |
| `cur_ac_lo`  | Vector{`T2`}    | 電流センサー：エアコンファン低 [A]                |
| `cur_tank`   | Vector{`T2`}    | 電流センサー：キャビン燃料ポンプ [A]               |
| `cur_flap`   | Vector{`T2`}    | 電流センサー：フラップモーター [A]                |
| `cur_strb`   | Vector{`T2`}    | 電流センサー：ストロボライト [A]                 |
| `cur_srvo_o` | Vector{`T2`}    | 電流センサー：INS外部サーボ [A]                |
| `cur_srvo_m` | Vector{`T2`}    | 電流センサー：INS中間サーボ [A]                |
| `cur_srvo_i` | Vector{`T2`}    | 電流センサー：INS内部サーボ [A]                |
| `cur_heat`   | Vector{`T2`}    | 電流センサー：INSヒーター [A]                 |
| `cur_acpwr`  | Vector{`T2`}    | 電流センサー：航空機電源 [A]                   |
| `cur_outpwr` | Vector{`T2`}    | 電流センサー：システム出力電力 [A]                |
| `cur_bat_1`  | Vector{`T2`}    | 電流センサー：バッテリー1 [A]                  |
| `cur_bat_2`  | Vector{`T2`}    | 電流センサー：バッテリー2 [A]                  |
| `vol_acpwr`  | Vector{`T2`}    | 電圧センサー：航空機電源 [V]                   |
| `vol_outpwr` | Vector{`T2`}    | 電圧センサー：システム出力電力 [V]                |
| `vol_bat_1`  | Vector{`T2`}    | 電圧センサー：バッテリー1 [V]                  |
| `vol_bat_2`  | Vector{`T2`}    | 電圧センサー：バッテリー2 [V]                  |
| `vol_res_p`  | Vector{`T2`}    | 電圧センサー：レゾルバーボード（+） [V]             |
| `vol_res_n`  | Vector{`T2`}    | 電圧センサー：レゾルバーボード（-） [V]             |
| `vol_back_p` | Vector{`T2`}    | 電圧センサー：バックプレーン（+） [V]              |
| `vol_back_n` | Vector{`T2`}    | 電圧センサー：バックプレーン（-） [V]              |
| `vol_gyro_1` | Vector{`T2`}    | 電圧センサー：ジャイロスコープ1 [V]               |
| `vol_gyro_2` | Vector{`T2`}    | 電圧センサー：ジャイロスコープ2 [V]               |
| `vol_acc_p`  | Vector{`T2`}    | 電圧センサー：INS加速度計（+） [V]              |
| `vol_acc_n`  | Vector{`T2`}    | 電圧センサー：INS加速度計（-） [V]              |
| `vol_block`  | Vector{`T2`}    | 電圧センサー：ブロック [V]                    |
| `vol_back`   | Vector{`T2`}    | 電圧センサー：バックプレーン [V]                 |
| `vol_srvo`   | Vector{`T2`}    | 電圧センサー：サーボ [V]                     |
| `vol_cabt`   | Vector{`T2`}    | 電圧センサー：キャビネット [V]                  |
| `vol_fan`    | Vector{`T2`}    | 電圧センサー：冷却ファン [V]                   |
| `aux_1`      | Vector{`T2`}    | 柔軟に使用できる補助データ1                     |
| `aux_2`      | Vector{`T2`}    | 柔軟に使用できる補助データ2                     |
| `aux_3`      | Vector{`T2`}    | 柔軟に使用できる補助データ3                     |

```
