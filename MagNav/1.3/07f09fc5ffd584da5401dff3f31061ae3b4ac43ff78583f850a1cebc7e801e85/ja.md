```
create_mag_c(path::Path, mapS::Union{MapS,MapSd,MapS3D} = get_map(namad);
             meas_var     = 1.0^2,
             fogm_sigma   = 1.0,
             fogm_tau     = 600.0,
             silent::Bool = false)
```

スカラー磁気異常マップから補正された（クリーンな）スカラー磁力計測定を作成します。

**引数:**

  * `path`:       `Path` 構造体、すなわち `Traj` 軌道構造体、`INS` 慣性航法システム構造体、または `FILTout` フィルタ抽出出力構造体
  * `mapS`:       （オプション）`MapS`、`MapSd`、または `MapS3D` スカラー磁気異常マップ構造体
  * `meas_var`:   （オプション）測定（ホワイト）ノイズ分散 [nT^2]
  * `fogm_sigma`: （オプション）FOGM キャッチオールバイアス [nT]
  * `fogm_tau`:   （オプション）FOGM キャッチオール時間定数 [s]
  * `silent`:     （オプション）true の場合、出力なし

**戻り値:**

  * `mag_c`: 補正された（クリーンな）スカラー磁力計測定 [nT]
