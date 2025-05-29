```
next_transition_instant(zdt::ZonedDateTime) -> Union{ZonedDateTime, Nothing}
next_transition_instant(tz::TimeZone=localzone()) -> Union{ZonedDateTime, Nothing}
```

Determine the next instant at which a time zone transition occurs (typically due to daylight-savings time). If no there exists no future transition then `nothing` will be returned.

Note that the provided `ZonedDateTime` isn't normally constructable:

```julia
julia> instant = next_transition_instant(ZonedDateTime(2018, 3, 1, tz"Europe/London"))
2018-03-25T01:00:00+00:00

julia> instant - Millisecond(1)  # Instant prior to the change
2018-03-25T00:59:59.999+00:00

julia> instant - Millisecond(0)  # Instant after the change
2018-03-25T02:00:00+01:00

julia> ZonedDateTime(2018, 3, 25, 1, tz"Europe/London")  # Cannot normally construct the `instant`
ERROR: NonExistentTimeError: Local DateTime 2018-03-25T01:00:00 does not exist within Europe/London
...
```
