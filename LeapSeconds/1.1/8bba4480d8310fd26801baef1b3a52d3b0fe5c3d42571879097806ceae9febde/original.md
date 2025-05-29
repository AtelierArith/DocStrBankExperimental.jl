```
offset_utc_tai(utc1, utc2=0.0)
```

Returns the difference between Coordinated Universal Time (UTC) and International Atomic Time (TAI) for a given UTC pseudo-Julian day number `utc1` (optionally split into two parts for increased precision).

$\Delta AT = UTC - TAI$

!!! note
    This function uses the [ERFA convention](https://github.com/liberfa/erfa/blob/master/src/dtf2d.c#L49) for Julian day numbers representing UTC dates during leap seconds.

