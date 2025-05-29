```
datetime(dt::NanosecondDateTime) -> ::Dates.DateTime
```

Return the date and time of `dt`, rounded down to the nearest millisecond. Add on the number of [`nanoseconds`](@ref LibMseed.nanoseconds) to obtain the full-precision time.

# Example

```
julia> ndt = NanosecondDateTime("2000-01-01T01:23:45.999999999")
NanosecondDateTime("2000-01-01T01:23:45.999999999")

julia> datetime(ndt)
2000-01-01T01:23:45.999
```

See also: [`NanosecondDateTime`](@ref), [`nearest_datetime`](@ref).
