```
create_mag_c(lat, lon, mapS::Union{MapS,MapSd,MapS3D} = get_map(namad);
             alt          = 1000,
             dt           = 0.1,
             meas_var     = 1.0^2,
             fogm_sigma   = 1.0,
             fogm_tau     = 600.0,
             silent::Bool = false)
```

スカラー磁気異常マップから補正された（クリーンな）スカラー磁力計測定値を作成します。

**引数:**

  * `lat`:        緯度  [ラジアン]
  * `lon`:        経度 [ラジアン]
  * `mapS`:       （オプション）`MapS`、`MapSd`、または`MapS3D`スカラー磁気異常マップ構造体
  * `alt`:        （オプション）高度  [メートル]
  * `dt`:         （オプション）測定時間ステップ [秒]
  * `meas_var`:   （オプション）測定（ホワイト）ノイズ分散 [nT^2]
  * `fogm_sigma`: （オプション）FOGMのバイアス [nT]
  * `fogm_tau`:   （オプション）FOGMの時間定数 [秒]
  * `silent`:     （オプション）trueの場合、出力なし

**戻り値:**

  * `mag_c`: 補正された（クリーンな）スカラー磁力計測定値 [nT]
