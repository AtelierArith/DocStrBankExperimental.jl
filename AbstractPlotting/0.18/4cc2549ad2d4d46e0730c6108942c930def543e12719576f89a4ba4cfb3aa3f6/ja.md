```
violin(x, y; kwargs...)
```

バイオリンプロットを描画します。

# 引数

  * `x`: カテゴリの位置
  * `y`: 密度が計算される変数

# キーワード

  * `orientation=:vertical`: バイオリンの向き（`:vertical` または `:horizontal`）
  * `width=0.8`: バイオリンの幅
  * `show_median=true`: 中央値を中線として表示
  * `side=:both`: バイオリンを片側のみにプロットするために `:left` または `:right` を指定
  * `datalimits`: `violin` をトリミングする値を指定します。`Tuple` または `Function`（例：`datalimits=extrema`）であることができます。
