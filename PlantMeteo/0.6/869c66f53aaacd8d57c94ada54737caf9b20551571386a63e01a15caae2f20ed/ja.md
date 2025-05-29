```
get_weather(lat, lon, period::Union{StepRange{Date, Day}, Vector{Dates.Date}}; api::DataType=OpenMeteo, sink=TimeStepTable, kwargs...)
```

指定された場所と時間の天気予報を天気APIを使用して返します。

# 引数

  * `lat::Float64`: 場所の緯度（度単位）
  * `lon::Float64`: 場所の経度（度単位）
  * `period::Union{StepRange{Date, Day}, Vector{Dates.Date}}`: 予報の期間
  * `api::DataType=OpenMeteo`: 予報に使用するAPI。
  * `sink::DataType=TimeStepTable`: 出力のタイプ。デフォルトは`TimeStepTable`ですが、

`DataFrames`など、`Tables.jl`インターフェースを実装する任意のタイプにすることができます。

  * `kwargs...`: APIに渡される追加のキーワード引数

# 詳細

使用可能なすべてのAPIは`subtype(AbstractAPI)`を使用して取得できます。デフォルトの[`OpenMeteo`](@ref) APIは商業利用には無料ではないことに注意し、責任を持って使用する必要があります。

# 例

```julia
using PlantMeteo, Dates
# 今日と明日の予報:
period = [today(), today()+Dates.Day(1)]
w = get_weather(48.8566, 2.3522, period)
```
