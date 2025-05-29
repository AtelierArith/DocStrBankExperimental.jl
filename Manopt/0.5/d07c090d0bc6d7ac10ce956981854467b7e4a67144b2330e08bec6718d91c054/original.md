```
get_residuals(M::AbstractManifold, nlso::NonlinearLeastSquaresObjective, p)
get_residuals!(M::AbstractManifold, V, nlso::NonlinearLeastSquaresObjective, p)
```

Compute the vector of residuals $f_i(p)$, $i=1,…,m$ given the manifold `M`, the [`NonlinearLeastSquaresObjective`](@ref) `nlso` and a current point $p$ on `M`.
