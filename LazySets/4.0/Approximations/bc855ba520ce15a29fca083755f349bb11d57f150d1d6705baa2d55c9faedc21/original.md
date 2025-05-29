```
overapproximate(S::LazySet{N},
                ::Type{<:HPolygon},
                [ε]::Real=Inf) where {N}
```

Overapproximate a given 2D set using iterative refinement.

### Input

  * `S`        – two-dimensional bounded set
  * `HPolygon` – target set type
  * `ε`        – (optional, default: `Inf`) error tolerance
  * `prune`    – (optional, default: `true`) flag for removing redundant               constraints in the end

### Output

A polygon in constraint representation.

### Notes

The result is always a convex overapproximation of the input set.

If no error tolerance ε is given, or is `Inf`, the result is a box-shaped polygon. For convex input sets, the result is an ε-close polygonal overapproximation with respect to the Hausdorff distance.
