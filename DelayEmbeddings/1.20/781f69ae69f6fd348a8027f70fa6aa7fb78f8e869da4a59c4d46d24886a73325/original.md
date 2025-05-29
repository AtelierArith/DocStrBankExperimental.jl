```
mdop_embedding(s::Vector; kwargs...) → Y, τ_vals, ts_vals, FNNs, βS
```

MDOP (for "maximizing derivatives on projection") is a unified approach to properly embed a timeseries or a set of timeseries (`Dataset`) based on the paper of Chetan Nichkawde [^Nichkawde2013].

## Keyword arguments

  * `τs= 0:50`: Possible delay values `τs`. For each of the `τs`'s the β-statistic gets computed.
  * `w::Int = 1`: Theiler window (neighbors in time with index `w` close to the point, that are excluded from being true neighbors). `w=0` means to exclude only the point itself, and no temporal neighbors.
  * `fnn_thres::Real= 0.05`: A threshold value defining a sufficiently small fraction of false nearest neighbors, in order to the let algorithm terminate and stop the embedding procedure (`0 ≤ fnn_thres < 1).
  * `r::Real = 2`: The threshold for the tolerable relative increase of the distance between the nearest neighbors, when increasing the embedding dimension.
  * `max_num_of_cycles = 50`: The algorithm will stop after that many cycles no matter what.

## Description

The method works iteratively and gradually builds the final embedding `Y`. Based on the [`beta_statistic`](@ref) the algorithm picks an optimal delay value `τ` for each embedding cycle as the global maximum of `β`. In case of multivariate embedding, i.e. when embedding a set of time series (`s::Dataset`), the optimal delay value `τ` is chosen as the maximum from all maxima's of all considered `β`-statistics for each possible timeseries. The range of considered delay values is determined in `τs` and for the nearest neighbor search we respect the Theiler window `w`.

After each embedding cycle the FNN-statistic `FNNs` [^Hegger1999][^Kennel1992] is being checked and as soon as this statistic drops below the threshold `fnn_thres`, the algorithm terminates. In order to increase the practability of the method the algorithm also terminates when the FNN-statistic `FNNs` increases.

The final embedding is returned as `Y`. The chosen delay values for each embedding cycle are stored in the `τ_vals` and the according timeseries index chosen for the the respective according delay value in `τ_vals` is stored in `ts_vals`. `βS, FNNs` are returned for clarity and double-checking, since they are computed anyway. In case of multivariate embedding, `βS` will store all `β`-statistics for all available time series in each embedding cycle. To double-check the actual used `β`-statistics in an embedding cycle 'k', simply `βS[k][:,ts_vals[k+1]]`.

[^Nichkawde2013]: Nichkawde, Chetan (2013). [Optimal state-space reconstruction using derivatives on projected manifold. Physical Review E 87, 022905](https://doi.org/10.1103/PhysRevE.87.022905).

[^Hegger1999]: Hegger, Rainer and Kantz, Holger (1999). [Improved false nearest neighbor method to detect determinism in time series data. Physical Review E 60, 4970](https://doi.org/10.1103/PhysRevE.60.4970).

[^Kennel1992]: Kennel, M. B., Brown, R., Abarbanel, H. D. I. (1992). [Determining embedding dimension for state-space reconstruction using a geometrical construction. Phys. Rev. A 45, 3403](https://doi.org/10.1103/PhysRevA.45.3403).
