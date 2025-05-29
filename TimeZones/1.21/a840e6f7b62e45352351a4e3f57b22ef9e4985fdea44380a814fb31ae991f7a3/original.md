```
FixedTimeZone(::AbstractString) -> FixedTimeZone
```

Constructs a `FixedTimeZone` with a UTC offset from a string. Resulting `FixedTimeZone` will be named like "UTC±HH:MM[:SS]".

# Examples

```julia
julia> FixedTimeZone("UTC+6")
UTC+06:00

julia> FixedTimeZone("-1330")
UTC-13:30

julia> FixedTimeZone("15:45:21")
UTC+15:45:21
```
