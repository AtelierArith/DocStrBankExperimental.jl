```
hms2rad(hours, mins, secs)
hms2rad(parts)
hms2rad(input::AbstractString)
```

Convert (hours, minutes, seconds) tuple to radians. If a string is given, will parse with [`parse_hms`](@ref) first. If an angle is input will treat as a no-op.
