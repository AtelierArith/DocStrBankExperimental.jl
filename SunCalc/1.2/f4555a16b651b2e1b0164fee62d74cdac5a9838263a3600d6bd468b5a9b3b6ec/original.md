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

Calculate sunlight times for the given date and location. Return a `NamedTuple`      or `DataFrame`.

Available variables:

| Variable        | Description                                                              |
|:--------------- |:------------------------------------------------------------------------ |
| `sunrise`       | Sunrise (top edge of the sun appears on the horizon)                     |
| `sunriseEnd`    | Sunrise ends (bottom edge of the sun touches the horizon)                |
| `goldenHourEnd` | Morning golden hour (soft light, best time for photography) ends         |
| `solarNoon`     | Solar noon (sun is in the highest position)                              |
| `goldenHour`    | Evening golden hour starts                                               |
| `sunsetStart`   | Sunset starts (bottom edge of the sun touches the horizon)               |
| `sunset`        | Sunset (sun disappears below the horizon, evening civil twilight starts) |
| `dusk`          | Dusk (evening nautical twilight starts)                                  |
| `nauticalDusk`  | Nautical dusk (evening astronomical twilight starts)                     |
| `night`         | Night starts (dark enough for astronomical observations)                 |
| `nadir`         | Nadir (darkest moment of the night, sun is in the lowest position)       |
| `nightEnd`      | Night ends (morning astronomical twilight starts)                        |
| `nauticalDawn`  | Nautical dawn (morning nautical twilight starts)                         |
| `dawn`          | Dawn (morning nautical twilight ends, morning civil twilight starts)     |

# Examples

```julia
using Dates, SunCalc
getSunlightTimes(today(), 54, 9; keep=[:sunrise, :sunset])

using TimeZones
getSunlightTimes(Date(2000, 07, 01), 54, 9, tz"UTC-3")

using DataFrames
days = collect(Date(2000, 07, 01):Day(1):Date(2000, 12, 31))
getSunlightTimes(days, 54, 9)
```
