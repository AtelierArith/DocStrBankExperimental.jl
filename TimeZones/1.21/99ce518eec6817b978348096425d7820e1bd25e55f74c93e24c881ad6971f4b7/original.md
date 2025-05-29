```
today(tz::TimeZone) -> Date
```

Create the current `Date` in the specified `TimeZone`. Equivalent to `Date(now(tz))`.

See also: [`now(::TimeZone)`](@ref), [`todayat(::TimeZone)`](@ref).

# Examples

```julia
julia> a, b = now(tz"Pacific/Midway"), now(tz"Pacific/Apia")
(2017-11-09T03:47:04.226-11:00, 2017-11-10T04:47:04.226+14:00)

julia> a - b
0 milliseconds

julia> today(tz"Pacific/Midway"), today(tz"Pacific/Apia")
(2017-11-09, 2017-11-10)
```
