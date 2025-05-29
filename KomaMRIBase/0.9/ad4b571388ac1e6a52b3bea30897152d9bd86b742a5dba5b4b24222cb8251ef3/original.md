```
periodic = Periodic(period, asymmetry)
```

The `Periodic` function is a custom constructor for the `TimeCurve` struct. It allows defining time intervals that repeat periodically with a triangular period.  It includes a measure of asymmetry in order to recreate a asymmetric period.

# Arguments

  * `period`: (`::Real`, `[s]`, `=1.0`) period duration
  * `asymmetry`: (`::Real`, `=0.5`) temporal asymmetry factor. Between 0 and 1.

# Returns

  * `periodic`: (`::TimeCurve`) TimeCurve struct

# Examples

```julia-repl
julia> periodic = Periodic(period=1.0, asymmetry=0.2)
```

![Periodic](../assets/periodic.svg)
