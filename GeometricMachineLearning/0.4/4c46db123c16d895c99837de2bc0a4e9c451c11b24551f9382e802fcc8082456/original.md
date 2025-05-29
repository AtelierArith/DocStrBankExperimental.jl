```
projection_error(rs)
```

Compute the projection error for a [`HRedSys`](@ref).

# Arguments

If the full system has already been integrated, then the projection error can be computed quicker:

```julia
projection_error(rs, sol_full)
```

This saves the cost of again integrating the systems.
