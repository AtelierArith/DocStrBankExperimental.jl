```
lwc_area(Vector{LWCSimpleChartItem}; kw...) -> LWCChart
```

[`LWCChart`](@ref) オブジェクトを作成し、ラインチャート情報を含みます。各チャートノードを [`LWCSimpleChartItem`](@ref) を使用してカスタマイズできる一般的なメソッドです。

[`Area`](https://tradingview.github.io/lightweight-charts/docs/series-types#area) のラッパー関数です。

## キーワード引数

| 名前::型                                       | デフォルト (可能な値)                                                                      | 説明               |
|:------------------------------------------- |:--------------------------------------------------------------------------------- |:---------------- |
| `price_scale_id::LWC_PRICE_SCALE_ID`        | `LWC_LEFT` (`LWC_RIGHT`)                                                          | Y軸の表示側。          |
| `label_name::String`                        | `""`                                                                              | チャート名。           |
| `visible::Bool`                             | `true`                                                                            | チャートの可視性。        |
| `precision::Int64`                          | `2`                                                                               | Y軸値の小数点以下の桁数。    |
| `top_color::String`                         | `"rgba(46, 220, 135, 0.4)"`                                                       | エリアの上部の色。        |
| `bottom_color::String`                      | `"rgba(40, 221, 100, 0)"`                                                         | エリアの下部の色。        |
| `invert_filled_area::Bool`                  | `false`                                                                           | 色の反転表示。          |
| `line_color::String`                        | ランダムな色                                                                            | ラインの色。           |
| `line_style::LWC_LINE_STYLES`               | `LWC_SOLID` (`LWC_DOTTED`, `LWC_DASHED`, `LWC_LARGE_DASHED`, `LWC_SPARSE_DOTTED`) | ラインスタイル。         |
| `line_width::Int64`                         | `1`                                                                               | ラインの幅。           |
| `line_type::LWC_LINE_TYPES`                 | `LWC_SIMPLE` (`LWC_SIMPLE`, `LWC_STEP`, `LWC_CURVED`)                             | ラインのタイプ。         |
| `point_markers_visible::Bool`               | `false`                                                                           | ラインノード上のマーカーの表示。 |
| `point_markers_radius::Float64`             | `4.0`                                                                             | マーカーのサイズ。        |
| `crosshair_marker_visible::Bool`            | `true`                                                                            | カーソルのクロスヘアの可視性。  |
| `crosshair_marker_radius::Float64`          | `4.0`                                                                             | クロスヘアのサイズ。       |
| `crosshair_marker_border_color::String`     | `"#758696"`                                                                       | クロスヘアの境界線の色。     |
| `crosshair_marker_background_color::String` | `"#4c525e"`                                                                       | クロスヘアの背景色。       |
| `crosshair_marker_border_width::Float64`    | `2.0`                                                                             | クロスヘアの境界線の幅。     |
| `plugins::Vector{LWCPlugin}`                | `LWCPlugin[]`                                                                     | 追加のプラグイン。        |
