```
PlotPager(layout [, kwargs=NamedTuple()][; displayfunc=(plot, nplot)->display(plot)])
```

プロットをサブプロットに蓄積します。

`layout` は `Plots.jl` の `layout` キーワードに供給され、Int または Tuple (ny, nx) であることができます。詳細は [https://docs.juliaplots.org/latest/](https://docs.juliaplots.org/latest/) を参照してください。

オプション引数 `kwargs::NamedTuple` は、`plot` に渡される追加のキーワード引数を提供します（例: `(legend_background_color=nothing, )` はすべてのサブプロットの凡例を透明な背景に設定します）。

オプションのキーワード引数 `displayfunc::(plot, nplot)->display(plot)` は、プロットの画面を表示するために使用される関数を提供します。ここで `plot` は Plot オブジェクトであり、`nplot::Integer` はこの画面の連番です。

# 使用法

```
julia> pp = PlotPager((2,2))  # 1画面あたり4パネル (2行2列)
julia> pp(plot(1:3))  # 蓄積
julia> pp(:skip, plot(1:4), plot(1:5), plot(1:6))  # 1つのコマンドで複数のパネルを追加
julia> pp(:newpage) # 不完全な画面をフラッシュして新しいページを開始 (注意: これは常にシーケンスの最後に追加してください！)

julia> pp = PlotPager((2, 2); displayfunc=(plot, nplot)->savefig(plot, "plot_$nplot.png")) # デフォルトの表示の代わりにファイルに保存
```

# コマンド

  * `pp(p)`: プロット p を蓄積
  * `pp(:skip)`: 空のパネルを残す
  * `pp(:newpage)`: 空のパネルで埋めて新しいページを開始
  * `pp(p1, p2, ...)`: 1回の呼び出しで複数のプロット/コマンド
