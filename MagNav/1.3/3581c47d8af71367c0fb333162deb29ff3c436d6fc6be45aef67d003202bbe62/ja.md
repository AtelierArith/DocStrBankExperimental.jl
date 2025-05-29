```
plot_path!(p1::Plot, path::Path, ind = trues(path.N);
           lab::String        = "",
           Nmax::Int          = 5000,
           show_plot::Bool    = true,
           zoom_plot::Bool    = false,
           path_color::Symbol = :ignore)
```

既存のプロットに飛行経路をプロットします。

**引数:**

  * `p1`:         プロット（すなわち、地図）
  * `path`:       `Path` 構造体、すなわち、`Traj` 軌道構造体、`INS` 慣性航法システム構造体、または `FILTout` フィルタ抽出出力構造体
  * `ind`:        （オプション）選択されたデータインデックス
  * `lab`:        （オプション）データ（凡例）ラベル
  * `Nmax`:       （オプション）プロットされるデータポイントの最大数
  * `show_plot`:  （オプション）true の場合、プロットを表示
  * `zoom_plot`:  （オプション）true の場合、飛行経路にプロットをズーム
  * `path_color`: （オプション）経路の色 {`:ignore`,`:black`,`:gray`,`:red`,`:orange`,`:yellow`,`:green`,`:cyan`,`:blue`,`:purple`}

**戻り値:**

  * `nothing`: 飛行経路が `p1` にプロットされます
