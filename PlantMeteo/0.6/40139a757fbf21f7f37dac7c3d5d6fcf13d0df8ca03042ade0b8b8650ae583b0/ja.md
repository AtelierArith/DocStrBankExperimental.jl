```
get_forecast(params::OpenMeteo, lat, lon, period; verbose=true)
```

OpenMeteo.comから天気予報を返す関数

# 引数

  * `lat`: 場所の緯度
  * `lon`: 場所の経度
  * `period::Union{StepRange{Date, Day}, Vector{Dates.Date}}`: 予報の期間
  * `verbose`: `true`の場合、エラーや警告が発生した場合により多くの情報を印刷します。
  * `kwargs`: [`get_forecast`](@ref)に渡される追加のキーワード引数（このメソッドでは使用されません）。

# 例

```julia
using PlantMeteo, Dates
lat = 48.8566
lon = 2.3522
period = [Dates.today(), Dates.today()+Dates.Day(3)]
params = OpenMeteo()
get_forecast(params, lat, lon, period)
```
