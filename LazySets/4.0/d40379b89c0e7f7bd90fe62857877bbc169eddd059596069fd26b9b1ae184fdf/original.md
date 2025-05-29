```
project(cp::CartesianProduct{N,<:Interval,<:Union{VPolygon,VPolytope}
        block::AbstractVector{Int};
        [kwargs...]) where {N}
```

Concrete projection of the Cartesian product of an interval and a set in vertex representation.

### Input

  * `cp`    – Cartesian product of an interval and a `VPolygon` or a `VPolytope`
  * `block` – block structure, a vector with the dimensions of interest

### Output

A `VPolytope` representing the projection of the Cartesian product `cp` on the dimensions specified by `block`.
