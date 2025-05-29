```julia
TimeVal(sec, usec)
```

yields an instance of `TimeVal` for an integer number of seconds `sec` and an integer number of microseconds `usec` since the Epoch.

```julia
TimeVal(sec)
```

yields an instance of `TimeVal` with a, possibly fractional, number of seconds `sec` since the Epoch.  Argument can also be an instance of [`TimeSpec`](@ref).

Call `now(TimeVal)` to get the current time as an instance of `TimeVal`.

Addition and subtraction involving and instance of `TimeVal` yield a `TimeVal` result.  For instance:

```julia
now(TimeVal) + 3.4
```

yields a `TimeVal` instance with the current time plus `3.4` seconds.

```julia
typemin(TimeVal)
typemax(TimeVal)
```

respectively yield the minimum and maximum normalized time values for an instance of `TimeVal`.
