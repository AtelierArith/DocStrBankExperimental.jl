```
TimeZone(str::AbstractString) -> TimeZone
```

Constructs a `TimeZone` subtype based upon the string. If the string is a recognized standard time zone name then data is loaded from the compiled IANA time zone database. Otherwise the string is parsed as a fixed time zone.

A list of recognized standard and legacy time zones names can is available by running `timezone_names()`. Supported fixed time zone string formats can be found in docstring for [`FixedTimeZone(::AbstractString)`](@ref).

## Examples

```jldoctest
julia> TimeZone("Europe/Warsaw")
Europe/Warsaw (UTC+1/UTC+2)

julia> TimeZone("UTC")
UTC
```
