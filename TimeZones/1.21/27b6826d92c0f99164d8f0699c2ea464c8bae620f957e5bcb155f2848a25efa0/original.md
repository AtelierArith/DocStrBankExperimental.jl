```
all_timezones(criteria::Function) -> Vector{TimeZone}
```

Returns `TimeZone`s that match the given `criteria` function. The `criteria` function takes two parameters: UTC transition (`DateTime`) and transition zone (`FixedTimeZone`).

## Examples

Find all time zones which contain an absolute UTC offset greater than 15 hours:

```julia
all_timezones() do dt, zone
    abs(zone.offset.std) > Dates.Second(Dates.Hour(15))
end
```

Determine all time zones which have a non-hourly daylight saving time offset:

```julia
all_timezones() do dt, zone
    zone.offset.dst % Dates.Second(Dates.Hour(1)) != 0
end
```
