```
plot_path(lat, lon;
          lab::String        = "",
          dpi::Int           = 200,
          margin::Int        = 2,
          Nmax::Int          = 5000,
          show_plot::Bool    = true,
          zoom_plot::Bool    = true,
          path_color::Symbol = :ignore)
```

フライトパスをプロットします。

**引数:**

  * `lat`:        緯度  [rad]
  * `lon`:        経度 [rad]
  * `lab`:        (オプション) データ (凡例) ラベル
  * `dpi`:        (オプション) インチあたりのドット数 (画像解像度)
  * `margin`:     (オプション) プロット周囲のマージン [mm]
  * `Nmax`:       (オプション) プロットされるデータポイントの最大数
  * `show_plot`:  (オプション) true の場合、プロットを表示
  * `zoom_plot`:  (オプション) true の場合、フライトパスにプロットをズーム
  * `path_color`: (オプション) パスの色 {`:ignore`,`:black`,`:gray`,`:red`,`:orange`,`:yellow`,`:green`,`:cyan`,`:blue`,`:purple`}

**戻り値:**

  * `p1`: フライトパスのプロット
