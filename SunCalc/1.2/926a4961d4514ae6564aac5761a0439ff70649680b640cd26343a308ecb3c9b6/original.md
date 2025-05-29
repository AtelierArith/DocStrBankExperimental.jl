```
getMoonPosition(
    time::Union{DateTime,ZonedDateTime},
    lat::Real,
    lon::Real;
    keep=[:altitude, :azimuth, :distance, :parallacticAngle])
```

Calculate the sun position for the given time and location. Return a `NamedTuple`     or `DataFrame`.

Available variables:

| Variable           | Description                                |
|:------------------ |:------------------------------------------ |
| `altitude`         | Moon altitude above the horizon in radians |
| `azimuth`          | Moon azimuth in radians                    |
| `distance`         | Distance to moon in kilometres             |
| `parallacticAngle` | Parallactic angle of the moon in radians   |

# Examples

```julia
using Dates, SunCalc
getMoonPosition(DateTime(2000, 07, 01, 12, 00, 00), 54, 9)

getMoonPosition(now(), 54, 9; keep=[:altitude])
```
