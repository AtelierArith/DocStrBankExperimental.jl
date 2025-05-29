```
now(::Type{Epoch})
now(::Type{Epoch{S}}) where S<:TimeScale
```

Get the current date and time as an `Epoch`. The default time scale is TAI.

# Example

```julia-repl
julia> now(Epoch)
2021-04-11T13:20:29.160 TAI

julia> now(TDBEpoch)
2021-04-11T13:21:21.518 TDB
```
