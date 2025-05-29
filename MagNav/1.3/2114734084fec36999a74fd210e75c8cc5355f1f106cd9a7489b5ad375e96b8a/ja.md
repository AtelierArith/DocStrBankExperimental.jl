```
create_flux(lat, lon, mapV::MapV = get_map(emm720);
            Cnb          = repeat(I(3),1,1,length(lat)),
            alt          = 1000,
            dt           = 0.1,
            meas_var     = 1.0^2,
            fogm_sigma   = 1.0,
            fogm_tau     = 600.0,
            silent::Bool = false)
```

ベクトル磁気異常マップから補正された（クリーンな）ベクトル磁力計測定を作成します。

**引数:**

  * `lat`:        緯度  [rad]
  * `lon`:        経度 [rad]
  * `mapV`:       （オプション）`MapV` ベクトル磁気異常マップ構造体
  * `Cnb`:        （オプション）方向余弦行列（ボディからナビゲーション）[-]
  * `alt`:        （オプション）高度  [m]
  * `dt`:         （オプション）測定時間ステップ [s]
  * `meas_var`:   （オプション）測定（ホワイト）ノイズ分散 [nT^2]
  * `fogm_sigma`: （オプション）FOGM キャッチオールバイアス [nT]
  * `fogm_tau`:   （オプション）FOGM キャッチオール時間定数 [s]
  * `silent`:     （オプション）trueの場合、出力なし

**戻り値:**

  * `flux`: `MagV` ベクトル磁力計測定構造体
