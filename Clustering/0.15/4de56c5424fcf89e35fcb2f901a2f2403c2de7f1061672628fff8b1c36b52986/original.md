```
vmeasure(a, b; [β = 1.0]) -> Float64
```

V-measure between the two clusterings.

`a` and `b` can be either [`ClusteringResult`](@ref) instances or assignments vectors (`AbstractVector{<:Integer}`).

The `β` parameter defines trade-off between *homogeneity* and *completeness*:

  * if $β > 1$, *completeness* is weighted more strongly,
  * if $β < 1$, *homogeneity* is weighted more strongly.

# References

> Andrew Rosenberg and Julia Hirschberg, 2007. *V-Measure: A conditional entropy-based external cluster evaluation measure*

