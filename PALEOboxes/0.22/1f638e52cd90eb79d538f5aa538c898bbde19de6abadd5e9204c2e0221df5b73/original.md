```
do_deriv(dispatchlists, deltat::Float64=0.0)
do_deriv(dispatchlists, pa::ParameterAggregator, deltat::Float64=0.0)
```

Wrapper function to calculate entire derivative (initialize and do methods) in one call. `dispatchlists` is from [`create_dispatch_methodlists`](@ref).
