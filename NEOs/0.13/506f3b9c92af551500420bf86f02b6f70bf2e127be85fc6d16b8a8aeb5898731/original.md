```
fetch_radec_mpc(id::AbstractString)
```

Download MPC optical astrometry of NEO `id` and return the output as `Vector{RadecMPC{Float64}}`.

!!! reference
    MPC Observations API documentation:

    https://minorplanetcenter.net/mpcops/documentation/observations-api/.

