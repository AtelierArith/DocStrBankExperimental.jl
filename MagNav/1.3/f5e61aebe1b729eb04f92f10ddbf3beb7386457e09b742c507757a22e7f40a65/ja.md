```
plot_frequency(xyz::XYZ;
               ind                = trues(xyz.traj.N),
               field::Symbol      = :mag_1_uc,
               freq_type::Symbol  = :PSD,
               detrend_data::Bool = true,
               window::Function   = hamming,
               dpi::Int           = 200,
               show_plot::Bool    = true,
               save_plot::Bool    = false,
               plot_png::String   = "PSD.png")
```

周波数データをプロットします。ウェルチのパワースペクトル密度（PSD）またはスペクトログラムのいずれかです。

**引数:**

  * `xyz`:          `XYZ` フライトデータ構造体
  * `ind`:          （オプション）選択されたデータインデックス
  * `field`:        （オプション）プロットする `xyz` のデータフィールド
  * `freq_type`:    （オプション）周波数プロットタイプ {`:PSD`,`:psd`,`:spectrogram`,`:spec`}
  * `detrend_data`: （オプション）true の場合、プロットデータのトレンドを除去
  * `window`:       （オプション）使用するウィンドウのタイプ
  * `dpi`:          （オプション）ドット毎インチ（画像解像度）
  * `show_plot`:    （オプション）true の場合、`p1` を表示
  * `save_plot`:    （オプション）true の場合、`p1` を `plot_png` として保存
  * `plot_png`:     （オプション）保存するプロットファイル名（`.png` 拡張子はオプション）

**戻り値:**

  * `p1`: ウェルチのパワースペクトル密度（PSD）またはスペクトログラムのプロット
