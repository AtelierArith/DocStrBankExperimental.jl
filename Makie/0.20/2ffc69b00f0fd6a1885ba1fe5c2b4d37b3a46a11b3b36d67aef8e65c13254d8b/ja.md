```
violin(x, y; kwargs...)
```

バイオリンプロットを描画します。

# 引数

  * `x`: カテゴリの位置
  * `y`: 密度が計算される変数

# キーワード

  * `weights`: 統計的重みのベクトル（データの長さ）。デフォルトでは、各観測値の重みは `1` です。
  * `orientation=:vertical`: バイオリンの向き（`:vertical` または `:horizontal`）
  * `width=1`: 縮小前のボックスの幅
  * `gap=0.2`: 縮小係数、`width -> width * (1 - gap)`
  * `show_median=false`: 中央値を中線として表示
  * `side=:both`: バイオリンを片側のみにプロットするために `:left` または `:right` を指定
  * `datalimits`: `violin` をトリミングする値を指定します。`Tuple` または `Function`（例：`datalimits=extrema`）であることができます。
