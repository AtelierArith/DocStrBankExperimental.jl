```
exponential(times, p)
```

Return volumes for specified `times`, based on the analytic solution to the exponential model for lesion growth. Here `p` will have properties `v0` and `ω`, where `v0` is the volume at time `times[1]` and `log(2)/ω` is the half life. Use negative `ω` for growth and positive `ω` for decay.

# Underlying ODE

In the exponential model, the volume $v > 0$ evolves according to the differential equation

$dv/dt = -ω v.$

For a list of all models see [`TumorGrowth`](@ref). 
