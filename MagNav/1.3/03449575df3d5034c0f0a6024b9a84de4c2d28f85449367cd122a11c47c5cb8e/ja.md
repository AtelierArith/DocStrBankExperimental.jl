```
plot_correlation(x::Vector, y::Vector,
                 xfeature::Symbol = :feature_1,
                 yfeature::Symbol = :feature_2;
                 lim::Real        = 0,
                 dpi::Int         = 200,
                 show_plot::Bool  = true,
                 save_plot::Bool  = false,
                 plot_png::String = "$xfeature-$yfeature.png",
                 silent::Bool     = true)
```

2つの特徴量の相関をプロットします。

**引数:**

  * `x`:         x軸データ
  * `y`:         y軸データ
  * `xfeature`:  x軸特徴名
  * `yfeature`:  y軸特徴名
  * `lim`:       （オプション）ピアソン相関係数が `lim` を超える場合のみプロット
  * `dpi`:       （オプション）ドット毎インチ（画像解像度）
  * `show_plot`: （オプション）trueの場合、`p1`を表示
  * `save_plot`: （オプション）trueの場合、`p1`を`plot_png`として保存
  * `plot_png`:  （オプション）保存するプロットファイル名（`.png`拡張子はオプション）
  * `silent`:    （オプション）trueの場合、出力なし

**戻り値:**

  * `p1`: `yfeature`対`xfeature`の相関のプロット
