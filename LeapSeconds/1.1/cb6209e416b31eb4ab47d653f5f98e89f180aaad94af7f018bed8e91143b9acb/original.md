```
offset_utc_tai(dt::DateTime)
```

Returns the difference between Coordinated Universal Time (UTC) and International Atomic Time (TAI) for a given `DateTime` in UTC.

$\Delta AT = UTC - TAI$

!!! warning
    The `DateTime` type from Julia's Standard Libary cannot represent UTC dates during leap seconds, e.g. "2016-12-31T23:59:60.0" will not be parsed as a valid `DateTime` but throw an error. The [AstroTime.jl](https://github.com/JuliaAstro/AstroTime.jl) package provides a leap second-aware `Epoch` type that can be used as a replacement.

