```
getSunPosition(
    time::Union{DateTime,ZonedDateTime}
    lat::Real,
    lon::Real;
    keep=[:altitude, :azimuth])
```

Calculate the sun position for the given time and location. Return a `NamedTuple`     or `DataFrame`.

Available variables:

| Variable   | Description                                                                                                                 |
|:---------- |:--------------------------------------------------------------------------------------------------------------------------- |
| `altitude` | Sun altitude above the horizon in radians, e.g. 0 at the horizon and π/2 at the zenith (straight over your head)            |
| `azimuth`  | Sun azimuth in radians (direction along the horizon, measured from south to west), e.g. 0 is south and π * 3/4 is northwest |

# Examples

```julia
using Dates, SunCalc
getSunPosition(DateTime(2000, 07, 01, 12, 00, 00), 54, 9)

getSunPosition(now(), 54, 9; keep=[:altitude])
```
