```
LWCSimpleChartItem(time::Int64, value::Real; kw...)
LWCSimpleChartItem(time::TimeType, value::Real; kw...)
```

このデータ型を使用すると、チャートの各ポイントの色をカスタマイズできます。 [`lwc_line`](@ref)、[`lwc_area`](@ref)、[`lwc_baseline`](@ref)、および[`lwc_histogram`](@ref)メソッドでサポートされています。

## フィールド

  * `time::Int64`: データのUnix時間。
  * `value::Float64`: データの値。

## キーワード引数

| 名前::型                         | デフォルト (可能な値) | 説明          |
|:----------------------------- |:------------ |:----------- |
| `line_color::String`          | `nothing`    | 線の色。        |
| `top_color::String`           | `nothing`    | 上部の色。       |
| `bottom_color::String`        | `nothing`    | 下部の色。       |
| `top_fill_color_1::String`    | `nothing`    | 上部の塗りつぶし色1。 |
| `top_fill_color_2::String`    | `nothing`    | 上部の塗りつぶし色2。 |
| `top_line_color::String`      | `nothing`    | 上部の線の色。     |
| `bottom_fill_color_1::String` | `nothing`    | 下部の塗りつぶし色1。 |
| `bottom_fill_color_2::String` | `nothing`    | 下部の塗りつぶし色2。 |
| `bottom_line_color::String`   | `nothing`    | 下部の線の色。     |
| `color::String`               | `nothing`    | 色。          |
