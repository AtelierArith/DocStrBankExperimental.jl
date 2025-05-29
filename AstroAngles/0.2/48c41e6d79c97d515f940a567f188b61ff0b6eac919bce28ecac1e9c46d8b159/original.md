```
hms2deg(hours, mins, secs)
hms2deg(parts)
hms2deg(input::AbstractString)
```

Convert (hours, minutes, seconds) tuple to degrees. If a string is given, will parse with [`parse_hms`](@ref) first. If an angle is input will treat as a no-op.
