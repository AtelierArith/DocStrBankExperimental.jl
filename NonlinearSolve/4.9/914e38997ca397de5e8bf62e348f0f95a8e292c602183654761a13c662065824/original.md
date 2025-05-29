```
SpeedMappingJL(;
    σ_min = 0.0, stabilize::Bool = false, check_obj::Bool = false,
    orders::Vector{Int} = [3, 3, 2]
)
```

Wrapper over [SpeedMapping.jl](https://nicolasl-s.github.io/SpeedMapping.jl/) for solving Fixed Point Problems. We allow using this algorithm to solve root finding problems as well.

### Keyword Arguments

  * `σ_min`: Setting to `1` may avoid stalling (see [lepage2021alternating](@cite)).
  * `stabilize`: performs a stabilization mapping before extrapolating. Setting to `true` may improve the performance for applications like accelerating the EM or MM algorithms (see [lepage2021alternating](@cite)).
  * `check_obj`: In case of NaN or Inf values, the algorithm restarts at the best past iterate.
  * `orders`: determines ACX's alternating order. Must be between `1` and `3` (where `1` means no extrapolation). The two recommended orders are `[3, 2]` and `[3, 3, 2]`, the latter being potentially better for highly non-linear applications (see [lepage2021alternating](@cite)).

!!! note
    This algorithm is only available if `SpeedMapping.jl` is installed and loaded.

