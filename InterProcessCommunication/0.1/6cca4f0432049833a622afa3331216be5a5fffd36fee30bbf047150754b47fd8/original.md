```julia
TimeSpec(sec, nsec)
```

yields an instance of `TimeSpec` for an integer number of seconds `sec` and an integer number of nanoseconds `nsec` since the Epoch.

```julia
TimeSpec(sec)
```

yields an instance of `TimeSpec` for a, possibly fractional, number of seconds `sec` since the Epoch.  Argument can also be an instance of [`TimeVal`](@ref).

Call `now(TimeSpec)` to get the current time as an instance of `TimeSpec`.

Addition and subtraction involving and instance of `TimeSpec` yield a `TimeSpec` result.  For instance:

```julia
now(TimeSpec) + 3.4
```

yields a `TimeSpec` instance with the current time plus `3.4` seconds.

```julia
typemin(TimeSpec)
typemax(TimeSpec)
```

respectively yield the minimum and maximum normalized time values for an instance of `TimeSpec`.
