```
ZonedDateTime(str::AbstractString)
```

Construct a `ZonedDateTime` by parsing `str`. This method is designed so that `zdt == ZonedDateTime(string(zdt))` where `zdt` can be any `ZonedDateTime` object. Take note that this method will always create a `ZonedDateTime` with a `FixedTimeZone` which can result in different results with date/time arithmetic.

## Examples

```jltest
julia> zdt = ZonedDateTime(2025, 3, 8, 9, tz"America/New_York")
2025-03-08T09:00:00-05:00

julia> timezone(zdt)
America/New_York (UTC-5/UTC-4)

julia> zdt + Day(1)
2025-03-09T09:00:00-04:00

julia> pzdt = ZonedDateTime(string(zdt))
2025-03-08T09:00:00-05:00

julia> timezone(pzdt)
UTC-05:00

julia> pzdt + Day(1)
2025-03-09T09:00:00-05:00
```
