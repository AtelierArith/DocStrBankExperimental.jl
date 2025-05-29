```
LWCCandleChartItem(time::Int64, open::Real, high::Real, low::Real, close::Real; kw...)
LWCCandleChartItem(time::TimeType, open::Real, high::Real, low::Real, close::Real; kw...)
```

[`lwc_candlestick`](@ref) および [`lwc_bar`](@ref) メソッドのためのローソク足データの表現。

## フィールド

  * `time::Int64`
  * `open::Float64`
  * `high::Float64`
  * `low::Float64`
  * `close::Float64`

## キーワード引数

| 名前::型                  | デフォルト (可能な値) | 説明       |
|:---------------------- |:------------ |:-------- |
| `color::String`        | `nothing`    | ローソク足の色。 |
| `border_color::String` | `nothing`    | 枠線の色。    |
| `wick_color::String`   | `nothing`    | ヒゲの色。    |

```
