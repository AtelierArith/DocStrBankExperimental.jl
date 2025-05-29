```
lwc_histogram(Vector{LWCSimpleChartItem}; kw...) -> LWCChart
```

[`LWCChart`](@ref) オブジェクトを作成し、ラインチャート情報を含みます。各チャートノードを [`LWCSimpleChartItem`](@ref) を使用してカスタマイズできる一般的なメソッドです。

[`Histogram`](https://tradingview.github.io/lightweight-charts/docs/series-types#histogram) のラッパー関数です。

## キーワード引数

| 名前::型                                | デフォルト (可能な値)             | 説明                           |
|:------------------------------------ |:------------------------ |:---------------------------- |
| `price_scale_id::LWC_PRICE_SCALE_ID` | `LWC_LEFT` (`LWC_RIGHT`) | Y軸の表示側。                      |
| `label_name::String`                 | `""`                     | チャート名。                       |
| `visible::Bool`                      | `true`                   | チャートの可視性。                    |
| `precision::Int64`                   | `2`                      | Y軸値の小数点以下の桁数。                |
| `color::String`                      | ランダムカラー                  | ヒストグラムの色。                    |
| `base::Real`                         | `0.0`                    | 大きいまたは小さいヒストグラム値が位置する基準となる値。 |
| `plugins::Vector{LWCPlugin}`         | `LWCPlugin[]`            | 追加のプラグイン。                    |
