```
NanosecondDateTime(dt::DateTime)
```

Create a `NanosecondDateTime` from a `DateTime`, `dt`.

# Example

```
julia> using Dates

julia> dt = now()
2021-04-18T22:03:52.145

julia> ndt = NanosecondDateTime(dt)
NanosecondDateTime("2021-04-18T22:03:52.145000000")

julia> datetime(ndt) == dt
true
```
