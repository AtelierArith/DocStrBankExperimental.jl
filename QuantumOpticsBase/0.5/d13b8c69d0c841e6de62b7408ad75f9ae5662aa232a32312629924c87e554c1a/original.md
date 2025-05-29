```
time_restrict(op::TimeDependentSum, t_from, t_to)
time_restrict(op::TimeDependentSum, t_to)
```

Restrict a [`TimeDependentSum`](@ref) `op` to the time window `t_from <= t < t_to`, forcing it to be exactly zero outside that range of times. If `t_from` is not provided, it is assumed to be zero. Return a new [`TimeDependentSum`](@ref).
