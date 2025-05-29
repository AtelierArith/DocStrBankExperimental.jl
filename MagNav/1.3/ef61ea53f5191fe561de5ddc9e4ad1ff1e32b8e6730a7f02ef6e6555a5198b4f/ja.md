```
plot_mag_map(path::Path, mag, itp_mapS;
             lab::String        = "magnetometer",
             order::Symbol      = :magmap,
             dpi::Int           = 200,
             Nmax::Int          = 5000,
             detrend_data::Bool = true,
             show_plot::Bool    = true,
             save_plot::Bool    = false,
             plot_png::String   = "mag_vs_map.png")
```

スカラー磁力計測定値とマップ値をプロットします。

**引数:**

  * `path`:         `Path` 構造体、すなわち `Traj` 軌道構造体、`INS` 慣性航法システム構造体、または `FILTout` フィルタ抽出出力構造体
  * `mag`:          スカラー磁力計測定値 [nT]
  * `itp_mapS`:     スカラーマップ補間関数 (`f(lat,lon)` または `f(lat,lon,alt)`)
  * `lab`:          （オプション）磁力計データ（凡例）ラベル
  * `order`:        （オプション）プロット順序 {`:magmap`,`:mapmag`}
  * `dpi`:          （オプション）インチあたりのドット数（画像解像度）
  * `Nmax`:         （オプション）プロットされるデータポイントの最大数
  * `detrend_data`: （オプション）trueの場合、プロットデータのトレンドを除去
  * `show_plot`:    （オプション）trueの場合、`p1`を表示
  * `save_plot`:    （オプション）trueの場合、`p1`を`plot_png`として保存
  * `plot_png`:     （オプション）保存するプロットファイル名（`.png`拡張子はオプション）

**戻り値:**

  * `p1`: スカラー磁力計測定値とマップ値
