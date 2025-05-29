```
geom_rainclouds(aes(...), ...)
geom_rainclouds(plot::GGPlot, aes(...), ...)
```

"Raincloud" プロットは、（半）バイオリンプロット、ボックスプロット、散布図の組み合わせです。これら3つを組み合わせることで、特に大規模な N データセットに対して魅力的で情報豊かなビジュアルを作成できます。

# 引数

  * `plot::GGPlot`（オプション）：このジオムを追加するためのプロットオブジェクト。これは通常、@chain の一部として ggplot を作成するのを容易にするために使用されます。
  * `data`（DataFrame）：このジオムに使用するデータ。提供されない場合、ジオムは ggplot からデータを継承します。
  * `aes(...)`：マッピングに使用される DataFrame の列名
  * `inherit_aes`：ジオムは ggplot から aes を継承すべきか？
  * `...`：列にマッピングされていないオプション（Makie.RainClouds に渡されます）

# 必須の美的要素

  * `x`
  * `y`

# オプションの美的要素（[`aes`](@ref)を参照）

  * `color` / `colour`
  * `size`
  * `stroke`
  * `dodge`

# オプションの引数

  * `boxplot_nudge`：デフォルト 0.075。center_boxplot が false の場合、ボックスプロットが中心線からどれだけ離れて配置されるべきかを決定します。これはボックスプロットを再中心化するために使用される値です。
  * `boxplot_width`：デフォルト 0.1。ボックスプロットの幅を決定します。
  * `center_boxplot`：デフォルト true。ボックスプロットがカテゴリの中心に配置されるべきかどうかを決定します。
  * `cloud_width`：デフォルト 0.75。バイオリンの幅を決定します。
  * `clouds`：デフォルトバイオリン。有効な値：[violin, hist, nothing]clouds
  * `color` / `colour`：デフォルトは青ですが、パレットや aes によって変更される場合があります。
  * `dodge_gap`：デフォルト 0.01。ドッジされたボックス間のギャップを決定します。
  * `gap`：デフォルト 0.2。プロットの主要要素間の距離。
  * `hist_bins`：デフォルト 30。`clouds == hist` の場合、ヒストグラムのビンの数を決定します。
  * `markersize` / `size`：デフォルト 2。散布図のマーカーのサイズ。
  * `plot_boxplots`：デフォルト true。ボックスプロットをプロットするかどうかを決定します。
  * `show_boxplot_outliers`：デフォルト false。ボックスプロットに外れ値を表示するかどうかを決定します。
  * `show_median`：デフォルト true。ボックスプロットに中央値を表示するかどうかを決定します。
  * `side`：デフォルト :left。ポイントに対するバイオリンの側を決定します。
  * `strokewidth` / `stroke`：デフォルト 1。ボックスプロットの周りのストロークの幅。
  * `whisker_width`：デフォルト 0.5。ボックスプロットのひげの幅。

# 例

```julia
ggplot(penguins) +
    geom_rainclouds(@aes(x = species, y = bill_depth_mm/10, color = species), size = 5) +
    scale_y_continuous(labels = "{:.1f} cm") +
    labs(title = "種ごとのくちばしの深さ", x = "種", y = "くちばしの深さ") +
    theme_minimal()
```
