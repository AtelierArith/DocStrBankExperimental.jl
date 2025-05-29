```
hms2ha(hours, mins, secs)
hms2ha(parts)
hms2ha(input::AbstractString)
```

Convert (hours, minutes, seconds) tuple to hour angles. If a string is given, will parse with [`parse_hms`](@ref) first. If an angle is input will treat as a no-op.
