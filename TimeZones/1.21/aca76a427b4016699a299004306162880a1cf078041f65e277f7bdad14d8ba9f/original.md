```
FixedTimeZone(zdt::ZonedDateTime) -> FixedTimeZone
```

Construct a `FixedTimeZone` using the UTC offset for the timestamp provided by the `ZonedDateTime`. If the timezone used by the `ZonedDateTime` has UTC offsets that change over time the returned `FixedTimeZone` will vary based upon the timestamp.

See also: [`TimeZone(::ZonedDateTime)`](@ref).

# Example

```jldoctest
julia> zdt1 = ZonedDateTime(2014, 5, 30, 21, tz"America/New_York")
2014-05-30T21:00:00-04:00

julia> FixedTimeZone(zdt1)
EDT (UTC-4)

julia> zdt2 = ZonedDateTime(2014, 2, 18, 6, tz"America/New_York")
2014-02-18T06:00:00-05:00

julia> FixedTimeZone(zdt2)
EST (UTC-5)
```
