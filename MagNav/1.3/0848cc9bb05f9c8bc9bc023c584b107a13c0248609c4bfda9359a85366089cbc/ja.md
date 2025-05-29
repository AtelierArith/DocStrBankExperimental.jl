```
plot_path(path::Path, ind = trues(path.N);
          lab::String        = "",
          dpi::Int           = 200,
          margin::Int        = 2,
          Nmax::Int          = 5000,
          show_plot::Bool    = true,
          zoom_plot::Bool    = true,
          path_color::Symbol = :ignore)
```

飛行経路をプロットします。

**引数:**

  * `path`:       `Path` 構造体、すなわち `Traj` 軌道構造体、`INS` 慣性航法システム構造体、または `FILTout` フィルタ抽出出力構造体
  * `ind`:        （オプション）選択されたデータインデックス
  * `lab`:        （オプション）データ（凡例）ラベル
  * `dpi`:        （オプション）ドット毎インチ（画像解像度）
  * `margin`:     （オプション）プロット周囲のマージン [mm]
  * `Nmax`:       （オプション）プロットされるデータポイントの最大数
  * `show_plot`:  （オプション）true の場合、プロットを表示
  * `zoom_plot`:  （オプション）true の場合、飛行経路にプロットをズーム
  * `path_color`: （オプション）経路の色 {`:ignore`,`:black`,`:gray`,`:red`,`:orange`,`:yellow`,`:green`,`:cyan`,`:blue`,`:purple`}

**戻り値:**

  * `p1`: 飛行経路のプロット
