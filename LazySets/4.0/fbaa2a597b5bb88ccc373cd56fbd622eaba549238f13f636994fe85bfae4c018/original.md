```
project(cp::CartesianProduct{N,<:Interval,<:AbstractZonotope},
        block::AbstractVector{Int};
        [kwargs...]) where {N}
```

Concrete projection of the Cartesian product of an interval and a zonotopic set.

### Input

  * `cp`    – Cartesian product of an interval and a zonotopic set
  * `block` – block structure, a vector with the dimensions of interest

### Output

A zonotope representing the projection of the Cartesian product `cp` on the dimensions specified by `block`.
