```
varinfo(a, b) -> Float64
```

Compute the *variation of information* between the two clusterings of the same data points.

`a` and `b` can be either [`ClusteringResult`](@ref) instances or assignments vectors (`AbstractVector{<:Integer}`).

# References

> Meila, Marina (2003). *Comparing Clusterings by the Variation of Information.* Learning Theory and Kernel Machines: 173–187.

