```
lwc_candlestick(data::Vector{LWCCandleChartItem}; kw...) -> LWCChart
```

[`LWCChart`](@ref) オブジェクトを作成し、ローソク足チャート情報を含みます。各チャートノードを [`LWCCandleChartItem`](@ref) を使用してカスタマイズできる一般的なメソッドです。

[`Candlestick`](https://tradingview.github.io/lightweight-charts/docs/series-types#candlestick) のラッパー関数です。

## キーワード引数

| 名前::型                                | デフォルト (可能な値)             | 説明              |
|:------------------------------------ |:------------------------ |:--------------- |
| `price_scale_id::LWC_PRICE_SCALE_ID` | `LWC_LEFT` (`LWC_RIGHT`) | Y軸の表示側。         |
| `label_name::String`                 | `""`                     | チャート名。          |
| `visible::Bool`                      | `true`                   | チャートの可視性。       |
| `precision::Int64`                   | `2`                      | Y軸値の小数点以下の桁数。   |
| `up_color::String`                   | `"#26a69a"`              | 強気のキャンドル（上昇）の色。 |
| `down_color::String`                 | `"#ef5350"`              | 弱気のキャンドル（下降）の色。 |
| `wick_visible::Bool`                 | `true`                   | ヒゲの可視性。         |
| `border_visible::Bool`               | `true`                   | キャンドルの境界の可視性。   |
| `border_color::String`               | `"#378658"`              | キャンドルの境界の色。     |
| `border_up_color::String`            | `"#26a69a"`              | 強気のキャンドルの境界の色。  |
| `border_down_color::String`          | `"#ef5350"`              | 弱気のキャンドルの境界の色。  |
| `wick_color::String`                 | `"#737375"`              | ヒゲの色。           |
| `wick_up_color::String`              | `"#26a69a"`              | 強気のキャンドルのヒゲの色。  |
| `wick_down_color::String`            | `"#ef5350"`              | 弱気のキャンドルのヒゲの色。  |
| `plugins::Vector{LWCPlugin}`         | `LWCPlugin[]`            | 追加のプラグイン。       |
