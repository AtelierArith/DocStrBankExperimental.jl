```
lwc_bar(data::Vector{LWCCandleChartItem}; kw...) -> LWCChart
```

[`LWCChart`](@ref) オブジェクトを作成し、バーチャート情報を含みます。各チャートノードを [`LWCCandleChartItem`](@ref) を使用してカスタマイズできる一般的なメソッドです。

[`Bar`](https://tradingview.github.io/lightweight-charts/docs/series-types#bar) のラッパー関数です。

## キーワード引数

| 名前::型                                | デフォルト (可能な値)             | 説明              |
|:------------------------------------ |:------------------------ |:--------------- |
| `price_scale_id::LWC_PRICE_SCALE_ID` | `LWC_LEFT` (`LWC_RIGHT`) | Y軸の表示側。         |
| `label_name::String`                 | `""`                     | チャート名。          |
| `visible::Bool`                      | `true`                   | チャートの可視性。       |
| `precision::Int64`                   | `2`                      | Y軸値の小数点以下の桁数。   |
| `up_color::String`                   | `"#26a69a"`              | 強気のキャンドルの色（上昇）。 |
| `down_color::String`                 | `"#ef5350"`              | 弱気のキャンドルの色（下降）。 |
| `open_visible::Bool`                 | `true`                   | オープンティックの可視性。   |
| `thin_bars::Bool`                    | `true`                   | 薄いバー。           |
| `plugins::Vector{LWCPlugin}`         | `LWCPlugin[]`            | 追加のプラグイン。       |
