```
NanosecondDateTime(str)
```

Create a `NanosecondDateTime` from a string.  It must be in the standard format `"yyyy-mm-ddTHH:MM:SS.s"`.  (See [`Dates.DateFormat`](@ref) for a description of the fields.)  Note that nanosecond precision can be given, but need not be.

# Examples

```
julia> NanosecondDateTime("1990-01-02T03:04:05.123456789")
NanosecondDateTime("1990-01-02T03:04:05.123456789")

julia> NanosecondDateTime("2000-01-01")
NanosecondDateTime("2000-01-01T00:00:00.000000000")
```
