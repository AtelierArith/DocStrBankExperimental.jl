```
get_1d_reservoir(nc;
    L = 1.0,
    perm = 9.8692e-14, # 0.1 darcy
    poro = 0.1,
    area = 1.0,
    z_max = nothing
)
```

Utility function for setting up a 1D reservoir domain with `nc` cells and length `L`. The [`reservoir_domain`](@ref) function is generally preferred and this function is kept for backwards compatibility.
