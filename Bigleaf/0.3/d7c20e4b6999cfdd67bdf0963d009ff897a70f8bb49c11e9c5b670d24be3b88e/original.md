```
calc_sun_position_hor(datetime, lat, long)
```

Compute the Sun position at given time and observer coordinates in horizontal coordinates.

# Arguments:

  * `datetime`: time: Either a `ZonedDateTime`, or `DateTime` assumed in UTC
  * `lat`, `long`: latitude and longitude in degree

# Value

`NamedTuple`: sun position with entries of the same type as `lat` and `long`

  * `altitude`: angle above the horizon [rad].
  * `azimuth`: angle ange the horizon plane eastwards of north [rad]
  * `hourangle`: [rad] as output by AstroLib.eq2hor  Seems to represent time [day/2pi] after solar noon.   Value at local timezone noon provides (local time - solar time).
