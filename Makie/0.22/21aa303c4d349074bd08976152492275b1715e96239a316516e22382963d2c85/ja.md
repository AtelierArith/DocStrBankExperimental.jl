```
rainclouds!(ax, category_labels, data_array; plot_boxplots=true, plot_clouds=true, kwargs...)
```

バイオリン（/ヒストグラム）、ボックスプロット、および各データポイントを適切な間隔でプロットします。

# 引数

  * `ax`: すべてのプロットを配置するために使用される軸。
  * `category_labels`: 通常は `Vector{String}` で、`data_array` の各要素に対するラベル。
  * `data_array`: 通常は `Vector{Float64}` で、プロットするデータポイントを表すために使用される。

# キーワード

## プロットタイプ

`rainclouds` 関数のプロットタイプエイリアスは `RainClouds` です。

## 属性

**`boxplot_nudge`** =  `0.075`  — `center_boxplot` が `false` のとき、ボックスプロットが中心線からどれだけ離れて配置されるべきかを決定します。これはボックスプロットを再中心化するために使用される値です。

**`boxplot_width`** =  `0.1`  — カテゴリ軸上のボックスプロットの幅。

**`center_boxplot`** =  `true`  — ボックスプロットをカテゴリの中心に配置するかどうか。

**`cloud_width`** =  `0.75`  — バイオリンプロットのサイズを決定します。`violin` のキーワード引数の `width` に対応します。

**`clouds`** =  `violin`  — [`violin`, `hist`, `nothing`] クラウドプロットをどのように表示するか、バイオリンまたはヒストグラムプロットとして、または全く表示しないか。

**`color`** =  `@inherit patchcolor`  — 単一の色、または各ポイントに対する色のベクトル。

**`cycle`** =  `[:color => :patchcolor]`  — *ドキュメントは利用できません。*

**`dodge`** =  `automatic`  — 同じ x 位置に複数の横並びのボックスを作成するためのグループ変数の整数のベクトル（データの長さ）。

**`dodge_gap`** =  `0.01`  — ドッジされたボックス間の間隔。

**`gap`** =  `0.2`  — メイン軸上の要素間の距離（`orientation` に依存）。

**`hist_bins`** =  `30`  — `clouds=hist` の場合、ヒストグラム呼び出しに渡されるビンの数。

**`jitter_width`** =  `0.05`  — カテゴリ x 軸の絶対的な用語での散布図バーの幅を決定します。

**`markersize`** =  `2.0`  — 散布図に使用されるマーカーのサイズ。

**`n_dodge`** =  `automatic`  — ドッジするカテゴリの数（デフォルトは `maximum(dodge)`）。

**`orientation`** =  `:vertical`  — レインクラウドの向き（`:vertical` または `:horizontal`）。

**`plot_boxplots`** =  `true`  — データの分布を要約するためにボックスプロットを表示するかどうか。

**`show_boxplot_outliers`** =  `false`  — ボックスプロットの外れ値をポイントとして表示します（散布図と組み合わせると通常は混乱を招くため、デフォルトでは表示しません）。

**`show_median`** =  `true`  — ボックスプロットに中央値の値の線を持つかどうかを決定します。

**`side`** =  `:left`  — `:left` または `:right` の値を取ることができ、散布ポイントに対してバイオリンプロットがどこに配置されるかを決定します。

**`side_nudge`** =  `automatic`  — 散布図特有。デフォルト値は `plot_boxplots` が true の場合は 0.02、そうでない場合はデフォルトで `0.075`。

**`strokewidth`** =  `1.0`  — ボックスプロットのアウトラインのストローク幅を決定します。

**`violin_limits`** =  `(-Inf, Inf)`  — `violin` をトリミングするための値を指定します。`Tuple` または `Function`（例：`datalimits=extrema`）であることができます。

**`whiskerwidth`** =  `0.5`  — ボックスプロットの Q1、Q3 のひげの幅。`boxplot_width` の一部としての値。
