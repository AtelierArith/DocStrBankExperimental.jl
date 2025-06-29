```
getMoonIllumination(
    time::Union{Date,DateTime,ZonedDateTime};
    keep=[:fraction, :phase, :angle])
```

Calculate moon illumination for the given time. Return a `NamedTuple` or `DataFrame`.

Available variables:

| Variable   | Description                                                                                                                                                                           |
|:---------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `fraction` | Illuminated fraction of the moon; varies from 0.0 (new moon) to 1.0 (full moon)                                                                                                       |
| `phase`    | Moon phase; varies from 0.0 to 1.0, described below                                                                                                                                   |
| `angle`    | Midpoint angle in radians of the illuminated limb of the moon reckoned eastward from the north point of the disk; the moon is waxing if the angle is negative, and waning if positive |

Moon phase value should be interpreted like this:

  * `0`: New Moon
  * *Waxing Crescent*
  * `0.25`: First Quarter
  * *Waxing Gibbous*
  * `0.5`: Full Moon
  * *Waning Gibbous*
  * `0.75`: Last Quarter
  * *Waning Crescent*

# Examples

```julia
using Dates, SunCalc
getMoonIllumination(Date(2000, 07, 01))

getMoonIllumination(now(), keep=[:fraction])
```
