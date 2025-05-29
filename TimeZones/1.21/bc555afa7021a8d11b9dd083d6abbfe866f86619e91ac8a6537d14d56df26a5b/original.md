```
todayat(tod::Time, tz::TimeZone, [amb::Union{Integer,Bool}]) -> ZonedDateTime
```

Creates a `ZonedDateTime` for today at the specified time of day. If the result is ambiguous in the given `TimeZone` then `amb` can be supplied to resolve ambiguity.

See also: [`now(::TimeZone)`](@ref), [`today(::TimeZone)`](@ref).

# Examples

```julia
julia> today(tz"Europe/Warsaw")
2017-10-29

julia> todayat(Time(10, 30), tz"Europe/Warsaw")
2017-10-29T10:30:00+01:00

julia> todayat(Time(2), tz"Europe/Warsaw")
ERROR: AmbiguousTimeError: Local DateTime 2017-10-29T02:00:00 is ambiguous within Europe/Warsaw

julia> todayat(Time(2), tz"Europe/Warsaw", 1)
2017-10-29T02:00:00+02:00

julia> todayat(Time(2), tz"Europe/Warsaw", 2)
2017-10-29T02:00:00+01:00
```
