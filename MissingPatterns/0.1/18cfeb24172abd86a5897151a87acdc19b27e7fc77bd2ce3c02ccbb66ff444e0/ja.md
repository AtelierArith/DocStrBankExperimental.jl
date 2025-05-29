plotmissing(df; plot*size=(1000, 800), orientation=:vertical, dpi=100, color*missing=:grey10, color*present=:white, line*color=:white, line*width=1, tick*step=5)

データフレーム内の欠損値パターンを示すヒートマップをプロットします。

# 引数

  * `df`: 入力データフレーム。
  * `plot_size`: プロットのサイズを指定するタプル。
  * `orientation`: ヒートマップの向き（`:vertical` または `:horizontal`）。
  * `dpi`: プロットの解像度。
  * `color_missing`: 欠損値の色。
  * `color_present`: 存在する値の色。
  * `line_color`: グリッド線の色。
  * `line_width`: グリッド線の幅。
  * `tick_step`: 軸の目盛りのステップサイズ。

# 戻り値

  * ヒートマッププロット。
