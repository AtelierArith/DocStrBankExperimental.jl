```
getSunlightTimes(
    date::Date, 
    lat::Real,
    lon::Real,
    tz::TimeZone; 
    keep=[:solarNoon, :nadir, :sunrise, :sunset, :sunriseEnd,
    :sunsetStart, :dawn, :dusk, :nauticalDawn, :nauticalDusk,
    :nightEnd, :night, :goldenHourEnd, :goldenHour])
```

指定された日付と場所のための太陽光時間を計算します。`NamedTuple`または`DataFrame`を返します。

利用可能な変数:

| 変数              | 説明                             |
|:--------------- |:------------------------------ |
| `sunrise`       | 日の出（太陽の上端が地平線に現れる）             |
| `sunriseEnd`    | 日の出終了（太陽の下端が地平線に触れる）           |
| `goldenHourEnd` | 朝のゴールデンアワー（柔らかい光、写真撮影に最適な時間）終了 |
| `solarNoon`     | 太陽の正午（太陽が最も高い位置にある）            |
| `goldenHour`    | 夕方のゴールデンアワーが始まる                |
| `sunsetStart`   | 日没開始（太陽の下端が地平線に触れる）            |
| `sunset`        | 日没（太陽が地平線の下に消え、夕方の市民薄明が始まる）    |
| `dusk`          | 薄暮（夕方の海上薄明が始まる）                |
| `nauticalDusk`  | 海上薄暮（夕方の天文薄明が始まる）              |
| `night`         | 夜の始まり（天文観測に十分暗い）               |
| `nadir`         | ナディール（夜の最も暗い瞬間、太陽が最も低い位置にある）   |
| `nightEnd`      | 夜の終了（朝の天文薄明が始まる）               |
| `nauticalDawn`  | 海上の夜明け（朝の海上薄明が始まる）             |
| `dawn`          | 夜明け（朝の海上薄明が終了し、朝の市民薄明が始まる）     |

# 例

```julia
using Dates, SunCalc
getSunlightTimes(today(), 54, 9; keep=[:sunrise, :sunset])

using TimeZones
getSunlightTimes(Date(2000, 07, 01), 54, 9, tz"UTC-3")

using DataFrames
days = collect(Date(2000, 07, 01):Day(1):Date(2000, 12, 31))
getSunlightTimes(days, 54, 9)
```
