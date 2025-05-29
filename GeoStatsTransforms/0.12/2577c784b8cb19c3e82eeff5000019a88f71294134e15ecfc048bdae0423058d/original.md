```
GSC(k, m; σ=1.0, tol=1e-4, maxiter=10, weights=nothing)
```

Assign labels to rows of geotable using the Geostatistical Spectral Clustering (GSC) algorithm.

The number of clusters `k` and the multiplicative factor `m` for adjacent weights determine the resulting number of clusters.

## Options

  * `σ`       - Standard deviation for exponential model (default to `1.0`)
  * `tol`     - Tolerance of k-means algorithm (default to `1e-4`)
  * `maxiter` - Maximum number of iterations (default to `10`)
  * `weights` - Dictionary of weights for each variable (default to `nothing`)

## References

  * Romary et al. 2015. [Unsupervised classification of multivariate geostatistical data: Two algorithms](https://www.sciencedirect.com/science/article/pii/S0098300415001314)

## Notes

The algorithm implemented here is slightly different than the algorithm described in Romary et al. 2015. Instead of setting Wᵢⱼ = 0 when i <-/-> j, we simply magnify the weight by a multiplicative factor Wᵢⱼ *= m when i <–> j. This leads to dense matrices but also better results in practice.
