```
plot_correlation(xyz::XYZ,
                 xfeature::Symbol = :mag_1_c,
                 yfeature::Symbol = :mag_1_uc,
                 ind              = trues(xyz.traj.N);
                 lim::Real        = 0,
                 dpi::Int         = 200,
                 show_plot::Bool  = true,
                 save_plot::Bool  = false,
                 plot_png::String = "$xfeature-$yfeature.png",
                 silent::Bool     = true)
```

2つの特徴間の相関をプロットします。

**引数:**

  * `xyz`:       `XYZ` フライトデータ構造
  * `xfeature`:  x軸の特徴名
  * `yfeature`:  y軸の特徴名
  * `ind`:       （オプション）選択されたデータインデックス
  * `lim`:       （オプション）ピアソン相関係数が `lim` より大きい場合のみプロット
  * `dpi`:       （オプション）ドットパーインチ（画像解像度）
  * `show_plot`: （オプション）trueの場合、`p1`を表示
  * `save_plot`: （オプション）trueの場合、`p1`を`plot_png`として保存
  * `plot_png`:  （オプション）保存するプロットファイル名（`.png`拡張子はオプション）
  * `silent`:    （オプション）trueの場合、出力なし

**戻り値:**

  * `p1`: `yfeature` 対 `xfeature` の相関のプロット
