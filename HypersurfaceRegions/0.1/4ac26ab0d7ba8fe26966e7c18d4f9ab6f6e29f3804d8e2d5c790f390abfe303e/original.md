```
membership(regions_list::Vector{Region}, p::Union{Vector{Float64},Vector{Int64}})
```

Input the list of regions of the complement of hypersurface arrangements and a point p.  Outputs the region the point p belongs to.

Options:

  * `reltol = 1e-6`, `abstol = 1e-9`: parameters for the accuracy of the ODE solver.

```
