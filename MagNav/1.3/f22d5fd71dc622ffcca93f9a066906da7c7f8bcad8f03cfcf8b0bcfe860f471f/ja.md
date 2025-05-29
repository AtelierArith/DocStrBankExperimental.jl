```
plot_mag_map_err(path::Path, mag, itp_mapS;
                 lab::String        = "",
                 dpi::Int           = 200,
                 Nmax::Int          = 5000,
                 detrend_data::Bool = true,
                 show_plot::Bool    = true,
                 save_plot::Bool    = false,
                 plot_png::String   = "mag_map_err.png")
```

スカラー磁力計測定とマップ値の誤差をプロットします。

**引数:**

  * `path`:         `Path` 構造体、すなわち `Traj` 軌道構造体、`INS` 慣性航法システム構造体、または `FILTout` フィルタ抽出出力構造体
  * `mag`:          スカラー磁力計測定 [nT]
  * `itp_mapS`:     スカラー地図補間関数 (`f(lat,lon)` または `f(lat,lon,alt)`)
  * `lab`:          （オプション）データ（凡例）ラベル
  * `dpi`:          （オプション）ドット毎インチ（画像解像度）
  * `Nmax`:         （オプション）プロットされるデータポイントの最大数
  * `detrend_data`: （オプション）trueの場合、プロットデータのトレンドを除去
  * `show_plot`:    （オプション）trueの場合、`p1`を表示
  * `save_plot`:    （オプション）trueの場合、`p1`を`plot_png`として保存
  * `plot_png`:     （オプション）保存するプロットファイル名（`.png`拡張子はオプション）

**戻り値:**

  * `p1`: スカラー磁力計測定とマップ値の誤差
