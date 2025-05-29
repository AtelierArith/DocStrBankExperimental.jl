```
SLIC(k, m; tol=1e-4, maxiter=10, weights=nothing)
```

Assign labels to rows of geotable using the Simple Linear Iterative Clustering (SLIC) algorithm.

The algorithm produces approximately `k` clusters by combining a geospatial distance `dₛ` and a distance between variables `dᵥ`. The tradeoff is controlled with a hyperparameter `m` in an additive model `dₜ = √(dᵥ² + m²(dₛ/s)²)` where `s` is the average spacing between cluster centroids.

## Options

  * `tol`     - Tolerance of k-means algorithm (default to `1e-4`)
  * `maxiter` - Maximum number of iterations (default to `10`)
  * `weights` - Dictionary with weights for each variable (default to `nothing`)

## References

  * Achanta et al. 2011. [SLIC superpixels compared to state-of-the-art superpixel methods](https://ieeexplore.ieee.org/document/6205760)

### Notes

The variables (or features) are standardized with the `StdFeats` transform prior to the core algorithm in order to facilitate the choice of the parameter `m`.
