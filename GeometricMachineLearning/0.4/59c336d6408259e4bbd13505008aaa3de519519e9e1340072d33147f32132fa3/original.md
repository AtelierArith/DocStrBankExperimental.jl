```
reduction_error(rs)
```

Compute the reduction error for a [`HRedSys`](@ref).

# Arguments

If the full system and the reduced system have already been integrated, then the reduction error can be computed quicker:

```julia
reduction_error(rs, sol_full, sol_reduced)
```

This saves the cost of again integrating the respective systems.
