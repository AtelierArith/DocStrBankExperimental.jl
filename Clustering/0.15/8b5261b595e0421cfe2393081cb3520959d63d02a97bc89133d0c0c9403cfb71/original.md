```
mutualinfo(a, b; normed=true) -> Float64
```

Compute the *mutual information* between the two clusterings of the same data points.

`a` and `b` can be either [`ClusteringResult`](@ref) instances or assignments vectors (`AbstractVector{<:Integer}`).

If `normed` parameter is `true` the return value is the normalized mutual information (symmetric uncertainty), see "Data Mining Practical Machine Tools and Techniques", Witten & Frank 2005.

# References

> Vinh, Epps, and Bailey, (2009). *Information theoretic measures for clusterings comparison*. Proceedings of the 26th Annual International Conference on Machine Learning - ICML ‘09.

