```
plot_basins_curves(fractions_cont [, prange]; kw...)
```

バシンの分数をパラメータ範囲/曲線に対してプロットします。つまり、[`global_continuation`](@ref)の出力を視覚化します。さらに、[`plot_basins_attractors_curves`](@ref)および[`plot_continuation_curves`](@ref)も参照してください。

## キーワード引数

  * `style = :band`: バシンの分数をどのように視覚化するか。選択肢は、累積和が1のバンドプロットのための`:band`または各バシン分数のラインプロットのための`:lines`です。
  * `separatorwidth = 1, separatorcolor = "white"`: スタイルが`:band`の場合、分数を区切る線を追加します。
  * `filler = NaN`: スタイルが`:lines`のとき、継続ステップで存在しないアトラクタIDのバシン分数に使用するフィラ値（`:band`スタイルではフィラは常に`0`です）。
  * `axislegend_kwargs = (position = :lt,)`: 凡例が追加される場合、`axislegend`に伝播されます。
  * `series_kwargs = NamedTuple()`: バンドまたはスキャッタラインプロットに伝播されます。
  * また、すべての[共通プロットキーワード](@ref common_plot_kwargs)。
