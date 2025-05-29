```
EmpiricalTransiogram(data, var; [options])
```

Computes the empirical (a.k.a. experimental) omnidirectional transiogram for categorical variable `var` stored in geospatial `data`.

## Options

  * nlags     - number of lags (default to `20`)
  * maxlag    - maximum lag in length units (default to 1/2 of minimum side of bounding box)
  * distance  - custom distance function (default to `Euclidean` distance)
  * algorithm - accumulation algorithm (default to `:ball`)

Available algorithms:

  * `:full` - loop over all pairs of points in the data
  * `:ball` - loop over all points inside maximum lag ball

All implemented algorithms produce the exact same result. The `:ball` algorithm is considerably faster when the maximum lag is much smaller than the bounding box of the domain of the data.

See also: [`DirectionalTransiogram`](@ref), [`PlanarTransiogram`](@ref), [`EmpiricalTransiogramSurface`](@ref).

## References

  * Carle, S.F. & Fogg, G.E. 1996. [Transition probability-based indicator geostatistics](https://link.springer.com/article/10.1007/BF02083656)
  * Carle et al 1998. [Conditional Simulation of Hydrofacies Architecture: A Transition Probability/Markov Approach](https://doi.org/10.2110/sepmcheg.01.147)
