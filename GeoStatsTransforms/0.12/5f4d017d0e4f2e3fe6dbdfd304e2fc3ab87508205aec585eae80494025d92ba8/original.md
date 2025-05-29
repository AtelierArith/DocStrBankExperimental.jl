```
GHC(k, λ; nmax=2000, kern=:epanechnikov, link=:ward)
```

Assign labels to rows of geotable using the Geostatistical Hierarchical Clustering (GHC) algorithm.

The approximate number of clusters `k` and the range `λ` of the `kern`el function determine the resulting number of clusters. The larger the range the more connected are nearby samples.

## Options

  * `nmax` - Maximum number of observations to use in distance matrix
  * `kern` - Kernel function (`:uniform`, `:triangular` or `:epanechnikov`)
  * `link` - Linkage function (`:single`, `:average`, `:complete`, `:ward` or `:ward_presquared`)

## References

  * Fouedjio, F. 2016. [A hierarchical clustering method for multivariate geostatistical data](https://www.sciencedirect.com/science/article/abs/pii/S2211675316300367)

### Notes

The range parameter controls the sparsity pattern of the pairwise distances, which can greatly affect the computational performance of the GHC algorithm. We recommend choosing a range that is small enough to connect nearby samples. For example, clustering data over a 100x100 Cartesian grid with unit spacing is possible with `λ=1.0` or `λ=2.0` but the problem starts to become computationally unfeasible around `λ=10.0` due to the density of points.
