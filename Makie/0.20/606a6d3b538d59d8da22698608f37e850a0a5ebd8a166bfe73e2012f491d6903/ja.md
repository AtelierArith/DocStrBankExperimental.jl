```
rainclouds!(ax, category_labels, data_array; plot_boxplots=true, plot_clouds=true, kwargs...)
```

バイオリン（/ヒストグラム）、箱ひげ図、個々のデータポイントを適切な間隔を持ってプロットします。

# 引数

  * `ax`: すべてのプロットを配置するために使用される軸。
  * `category_labels`: 通常は `Vector{String}` で、`data_array` の各要素に対するラベル。
  * `data_array`: 通常は `Vector{Float64}` で、プロットするデータポイントを表すために使用される。

# キーワード

  * `gap=0.2`: x軸の要素間の距離。
  * `side=:left`: `:left` または `:right` の値を取ることができ、バイオリンプロットが散布点に対してどこに配置されるかを決定します。
  * `dodge`: 同じx位置に複数の横並びの箱を作成するためのグループ化変数の整数ベクトル（データの長さ）。
  * `dodge_gap = 0.03`: ドッジされた箱の間の間隔。
  * `n_dodge`: ドッジするカテゴリの数（デフォルトは最大(dodge)）。
  * `color`: 単一の色、または各ポイントに対する色のベクトル。

## バイオリン/ヒストグラムプロット特有のキーワード

  * `clouds=violin`: バイオリンまたはヒストグラムプロットとしてクラウドプロットを表示するための [violin, hist, nothing]、またはクラウドプロットを表示しない。
  * `hist_bins=30`: `clouds=hist` の場合、ヒストグラム呼び出しに渡すビンの数。
  * `cloud_width=1.0`: バイオリンプロットのサイズを決定します。`violin` の `width` キーワード引数に対応します。
  * `orientation=:vertical`: レインクラウドの向き（`:vertical` または `:horizontal`）。
  * `violin_limits=(-Inf, Inf)`: `violin` をトリミングするための値を指定します。`Tuple` または `Function`（例：`datalimits=extrema`）であることができます。

## 箱ひげ図特有のキーワード

  * `plot_boxplots=true`: データの分布を要約するために箱ひげ図を表示するかどうかのブール値。
  * `boxplot_width=0.1`: カテゴリx軸の絶対的な箱ひげ図の幅。
  * `center_boxplot=true`: 箱ひげ図をカテゴリの中心に配置するかどうかを決定します。
  * `whiskerwidth=0.5`: 箱ひげ図のQ1、Q3のひげの幅。`boxplot_width`の一部としての値。
  * `strokewidth=1.0`: 箱ひげ図のアウトラインのストローク幅を決定します。
  * `show_median=true`: 箱ひげ図に中央値の値を示す線を持つかどうかを決定します。
  * `boxplot_nudge=0.075`: `center_boxplot`が`false`のとき、箱ひげ図が中心線からどれだけ離れて配置されるべきかを決定します。これは箱ひげ図を再中心化するために使用される値です。
  * `show_boxplot_outliers`: 箱ひげ図の外れ値をポイントとして表示します（散布図と組み合わせると通常は混乱を招くため、デフォルトでは表示しません）。

## 散布図特有のキーワード

  * `side_nudge`: デフォルト値は `plot_boxplots` が true の場合は 0.02、そうでない場合はデフォルトで 0.075。
  * `jitter_width=0.05`: カテゴリx軸の絶対的な散布図バーの幅を決定します。
  * `markersize=2`: 散布図に使用されるマーカーのサイズ。

## 軸一般キーワード

  * `title`
  * `xlabel`
  * `ylabel`

```
