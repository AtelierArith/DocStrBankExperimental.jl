```
n_statistic(Y, s; kwargs...) → N, d_E1
```

Perform one embedding cycle according to the method proposed in [^Garcia2005a] for a given phase space trajectory `Y` (of type `Dataset`) and a time series `s (of type`Vector`). Return the proposed N-Statistic`N`and all nearest neighbor distances`d_E1`for each point of the input phase space trajectory`Y`. Note that`Y` is a single time series in case of the first embedding cycle.

## Keyword arguments

  * `τs= 0:50`: Considered delay values `τs` (in sampling time units). For each of the `τs`'s the N-statistic gets computed.
  * `r = 10`: The threshold, which defines the factor of tolerable stretching for the d_E1-statistic (see algorithm description).
  * `T::Int = 1`: The forward time step (in sampling units) in order to compute the `d_E2`-statistic (see algorithm description). Note that in the paper this is not a free parameter and always set to `T=1`.
  * `w::Int = 0`: Theiler window (neighbors in time with index `w` close to the point, that are excluded from being true neighbors). `w=0` means to exclude only the point itself, and no temporal neighbors. Note that in the paper this is not a free parameter and always `w=0`.
  * `metric = Euclidean()`: metric used for finding nearest neigbhors in the input phase space trajectory `Y`.

## Description

For a range of possible delay values `τs` one constructs a temporary embedding matrix. That is, one concatenates the input phase space trajectory `Y` with the `τ`-lagged input time series `s`. For each point on the temporary trajectory one computes its nearest neighbor, which is denoted as the `d_E1`-statistic for a specific `τ`. Now one considers the distance between the reference point and its nearest neighbor `T` sampling units ahead and calls this statistic `d_E2`. [^Garcia2005a] strictly use `T=1`, so they forward each reference point and its corresponding nearest neighbor just by one (!) sampling unit. Here it is a free parameter.

The `N`-statistic is then the fraction of `d_E2`/`d_E1`-pairs which exceed a threshold `r`.

Plotted vs. the considered `τs`-values it is proposed to pick the `τ`-value for this embedding cycle as the value, where `N` has its first local minimum.

[^Garcia2005a]: Garcia, S. P., Almeida, J. S. (2005). [Nearest neighbor embedding with different time delays. Physical Review E 71, 037204](https://doi.org/10.1103/PhysRevE.71.037204).
