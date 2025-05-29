```
garcia_almeida_embedding(s; kwargs...) → Y, τ_vals, ts_vals, FNNs ,NS
```

A unified approach to properly embed a time series (`Vector` type) or a set of time series (`Dataset` type) based on the papers of Garcia & Almeida [^Garcia2005a],[^Garcia2005b].

## Keyword arguments

  * `τs= 0:50`: Possible delay values `τs` (in sampling time units). For each of the `τs`'s the N-statistic gets computed.
  * `w::Int = 1`: Theiler window (neighbors in time with index `w` close to the point, that are excluded from being true neighbors). `w=0` means to exclude only the point itself, and no temporal neighbors.
  * `r1 = 10`: The threshold, which defines the factor of tolerable stretching for the d_E1-statistic.
  * `r2 = 2`: The threshold for the tolerable relative increase of the distance between the nearest neighbors, when increasing the embedding dimension.
  * `fnn_thres= 0.05`: A threshold value defining a sufficiently small fraction of false nearest neighbors, in order to the let algorithm terminate and stop the embedding procedure (`0 ≤ fnn_thres < 1).
  * `T::Int = 1`: The forward time step (in sampling units) in order to compute the `d_E2`-statistic (see algorithm description). Note that in the paper this is not a free parameter and always set to `T=1`.
  * `metric = Euclidean()`: metric used for finding nearest neigbhors in the input phase space trajectory `Y`.
  * `max_num_of_cycles = 50`: The algorithm will stop after that many cycles no matter what.

## Description

The method works iteratively and gradually builds the final embedding vectors `Y`. Based on the `N`-statistic the algorithm picks an optimal delay value `τ` for each embedding cycle as the first local minimum of `N`. In case of multivariate embedding, i.e. when embedding a set of time series (`s::Dataset`), the optimal delay value `τ` is chosen as the first minimum from all minimum's of all considered `N`-statistics for each embedding cycle. The range of considered delay values is determined in `τs` and for the nearest neighbor search we respect the Theiler window `w`. After each embedding cycle the FNN-statistic `FNNs` [^Hegger1999][^Kennel1992] is being checked and as soon as this statistic drops below the threshold `fnn_thres`, the algorithm breaks. In order to increase the  practability of the method the algorithm also breaks, when the FNN-statistic `FNNs` increases . The final embedding vector is stored in `Y` (`Dataset`). The chosen delay values for each embedding cycle are stored in the `τ_vals` and the according time series number chosen for the according delay value in `τ_vals` is stored in `ts_vals`. For univariate embedding (`s::Vector`) `ts_vals` is a vector of ones of length `τ_vals`, because there is simply just one time series to choose from. The function also returns the `N`-statistic `NS` for each embedding cycle as an `Array` of `Vector`s.

Notice that we were *not* able to reproduce the figures from the papers with our implementation (which nevertheless we believe is the correct one).

[^Garcia2005a]: Garcia, S. P., Almeida, J. S. (2005). [Nearest neighbor embedding with different time delays. Physical Review E 71, 037204](https://doi.org/10.1103/PhysRevE.71.037204).

[^Garcia2005b]: Garcia, S. P., Almeida, J. S. (2005). [Multivariate phase space reconstruction by nearest neighbor embedding with different time delays. Physical Review E 72, 027205](https://doi.org/10.1103/PhysRevE.72.027205).
