```
nearest_datetime(dt::NanosecondDateTime) -> ::Dates.DateTime
```

Round `dt` to the nearest millisecond and return a `DateTime`.

# Example

```
julia> ndt = NanosecondDateTime("1999-12-31T23:59:59.9996")
NanosecondDateTime("1999-12-31T23:59:59.999600000")

julia> nearest_datetime(ndt)
2000-01-01T00:00:00
```

See also: [`datetime`](@ref).
