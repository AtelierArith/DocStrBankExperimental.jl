```
timezones_at(latitude, longitude)
```

Get the timezones used at the given `latitude` and `longitude`.

If no timezones are known, then an empty list will be returned. Conversely, if the co-ordinates land in a disputed region, all applicable timezones will be returned.

```jldoctest
julia> timezones_at(52.5061, 13.358)
1-element Vector{Dates.TimeZone}:
 Europe/Berlin (UTC+1/UTC+2)

julia> timezones_at(69.8, -141)
2-element Vector{Dates.TimeZone}:
 America/Anchorage (UTC-9/UTC-8)
 America/Dawson (UTC-7)
```

!!! note
    The library will use a version of the timezone-boundary-builder data that is compatible with the version of tzdata currently used by `TimeZones`.

    Nominally this will be the *same* version as is used by `TimeZones`, but in some cases an older version might be used.

    There are two possible reasons for this:

    ```
    1. There were no boundary changes in a tzdata release, which means that there will
        never be a boundary release for this particular version.
    2. The boundary dataset is not yet available for a new tzdata release.
    ```

