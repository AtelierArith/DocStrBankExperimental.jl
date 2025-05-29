```julia
log_with_time_derivative(t, twist)

```

Compute exponential coordinates as well as their time derivatives in one shot. This mainly exists because ForwardDiff won't work at the singularity of `log`. It is also ~50% faster than ForwardDiff in this case.
