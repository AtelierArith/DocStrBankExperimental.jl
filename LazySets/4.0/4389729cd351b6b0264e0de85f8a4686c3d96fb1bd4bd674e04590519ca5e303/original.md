```
project(cp::CartesianProduct{N,<:Interval,<:AbstractHyperrectangle},
        block::AbstractVector{Int};
        [kwargs...]) where {N}
```

Concrete projection of the Cartesian product of an interval and a hyperrectangular set.

### Input

  * `cp`    – Cartesian product of an interval and a hyperrectangle
  * `block` – block structure, a vector with the dimensions of interest

### Output

A hyperrectangle representing the projection of the Cartesian product `cp` on the dimensions specified by `block`.
