```
plot_path!(p1::Plot, lat, lon;
           lab::String        = "",
           Nmax::Int          = 5000,
           show_plot::Bool    = true,
           zoom_plot::Bool    = false,
           path_color::Symbol = :ignore)
```

既存のプロットに飛行経路をプロットします。

**引数:**

  * `p1`:         プロット（地図）
  * `lat`:        緯度  [ラジアン]
  * `lon`:        経度 [ラジアン]
  * `lab`:        （オプション）データ（凡例）ラベル
  * `Nmax`:       （オプション）プロットされるデータポイントの最大数
  * `show_plot`:  （オプション）trueの場合、プロットを表示
  * `zoom_plot`:  （オプション）trueの場合、飛行経路にプロットをズーム
  * `path_color`: （オプション）経路の色 {`:ignore`,`:black`,`:gray`,`:red`,`:orange`,`:yellow`,`:green`,`:cyan`,`:blue`,`:purple`}

**戻り値:**

  * `nothing`: `p1`に飛行経路がプロットされます
