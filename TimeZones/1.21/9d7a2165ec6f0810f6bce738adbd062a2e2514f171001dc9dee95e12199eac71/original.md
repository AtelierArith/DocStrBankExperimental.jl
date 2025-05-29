```
TimeZone(zdt::ZonedDateTime) -> TimeZone
```

Extract the `TimeZone` associated with the `ZonedDateTime`.

See also: [`timezone(::ZonedDateTime)`](@ref), [`FixedTimeZone(::ZonedDateTime)`](@ref).

# Examples

```jldoctest
julia> zdt = ZonedDateTime(2014, 5, 30, 21, tz"America/New_York")
2014-05-30T21:00:00-04:00

julia> TimeZone(zdt)
America/New_York (UTC-5/UTC-4)
```
