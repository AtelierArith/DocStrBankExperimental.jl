```
lefschetz_topboundary(lc::LefschetzComplex, subcomp::Vector{String})
```

Compute the topological boundary of a Lefschetz complex subset.

In contrast to the algebraic boundary defined via the boundary operator, this function computes the boundary of the Lefschetz complex subset specified in `subcomp` if the Lefschetz complex is interpreted as a finite topological space. In other words, the topological boundary is the set difference of the closure and the interior of the subset.
