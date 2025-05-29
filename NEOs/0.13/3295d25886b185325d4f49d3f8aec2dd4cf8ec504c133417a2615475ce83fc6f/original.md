```
fetch_radec_neocp(id::AbstractString)
```

Download MPC optical astrometry of NEOCP object `id` and return the output as `Vector{RadecMPC{Float64}}`.

!!! reference
    MPC NEOCP Observations API documentation:

    https://www.minorplanetcenter.net/mpcops/documentation/neocp-observations-api/.

