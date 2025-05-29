```
nanoseconds(dt::NanosecondDateTime) -> ::Dates.Nanosecond(n)
```

Return the number of additional nanoseconds of the date and time represented by `dt`, beyond the millisecond resolution of [`datetime`](@ref LibMseed.datetime). This value is always positive.

# Example

```
julia> ndt = NanosecondDateTime("1990-01-02T00:11:22.123456789")
NanosecondDateTime("1990-01-02T00:11:22.123456789")

julia> nanoseconds(ndt)
456789 nanoseconds
```

See also: [`NanosecondDateTime`](@ref).
