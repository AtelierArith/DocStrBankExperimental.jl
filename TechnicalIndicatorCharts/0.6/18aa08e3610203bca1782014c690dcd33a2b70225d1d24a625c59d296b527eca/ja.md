# 概要

Chartは、以下の要素を持つ可変構造体です。

  * 名前（通常は「BTCUSD」や「AAPL」などの資産名）
  * 時間枠（チャート上の各キャンドルが表す時間の長さを制御）
  * OHLCV値と指標値を保持するためのDataFrame
  * チャートに表示するための`OnlineTechnicalIndicator`のベクター
  * 各指標の表示設定のための別のベクター

[TradingView](https://tradingview.com/)に行ってチャートを見た場合、それをメモリ内で表現するために必要なデータ構造を想像してみてください。それが`Chart`構造体の目的です。

# フィールド

  * `name::AbstractString`
  * `tf::Dates.Period`
  * `indicators::AbstractVector{OnlineTechnicalIndicators.TechnicalIndicator}`
  * `visuals::AbstractVector`
  * `df::DataFrames.DataFrame`
  * `ts::Union{Missing, Dates.DateTime}`
  * `candle::Union{Missing, TechnicalIndicatorCharts.Candle}`

# コンストラクタ

```julia
Chart(name, tf; indicators=[], visuals=[])
```

# 例

```julia-repl
julia> just_candles = Chart("ETHUSD", Minute(1))

julia> golden_cross = Chart(
           "BTCUSD", Hour(4);
           indicators = [
               SMA{Float64}(;period=50),
               SMA{Float64}(;period=200)
           ],
           visuals = [
               Dict(
                   :label_name => "SMA 50",
                   :line_color => "#E072A4",
                   :line_width => 2
               ),
               Dict(
                   :label_name => "SMA 200",
                   :line_color => "#3D3B8E",
                   :line_width => 5
               )
           ]
       )

julia> default_visuals = Chart(
           "BNBUSDT", Hour(4);
           indicators = [BB{Float64}(), StochRSI{Float64}()],
           visuals    = [nothing,       nothing]  # デフォルトを使用するには、`nothing`を渡します。
       )
```
