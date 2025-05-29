```
randindex(a, b) -> NTuple{4, Float64}
```

Compute the tuple of Rand-related indices between the clusterings `c1` and `c2`.

`a` and `b` can be either [`ClusteringResult`](@ref) instances or assignments vectors (`AbstractVector{<:Integer}`).

Returns a tuple of indices:

  * Hubert & Arabie Adjusted Rand index
  * Rand index (agreement probability)
  * Mirkin's index (disagreement probability)
  * Hubert's index ($P(\mathrm{agree}) - P(\mathrm{disagree})$)

# References

> Lawrence Hubert and Phipps Arabie (1985). *Comparing partitions.* Journal of Classification 2 (1): 193-218


> Meila, Marina (2003). *Comparing Clusterings by the Variation of Information.* Learning Theory and Kernel Machines: 173-187.


> Steinley, Douglas (2004). *Properties of the Hubert-Arabie Adjusted Rand Index.* Psychological Methods, Vol. 9, No. 3: 386-396

