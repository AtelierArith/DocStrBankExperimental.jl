```
pecuzal_embedding(s; kwargs...) → Y, τ_vals, ts_vals, ΔLs, ⟨ε★⟩
```

A unified approach to properly embed a timeseries or a set of timeseries (`StateSpaceSet`) based on the recent PECUZAL algorithm due to Kraemer et al.[^Kraemer2021].

For more details, see the description below.

## Keyword arguments

  * `τs = 0:50`: Possible delay values `τs` (in sampling time units). For each of the `τs`'s the continuity statistic ⟨ε★⟩ gets computed and further processed in order to find optimal delays `τᵢ` for each embedding cycle `i`.
  * `w::Int = 0`: Theiler window (neighbors in time with index `w` close to the point, that are excluded from being true neighbors). `w=0` means to exclude only the point itself, and no temporal neighbors.
  * `samplesize::Real = 1.0`: Fraction of state space points to be considered (fiducial points v) to average ε★ over, in order to produce `⟨ε★⟩`. Lower fraction value decreases accuracy as well as computation time.
  * `K::Int = 13`: the amount of nearest neighbors in the δ-ball (read algorithm description). Must be at least 8 (in order to gurantee a valid statistic). `⟨ε★⟩` is computed taking the minimum result over all `k ∈ K`.
  * `KNN::Int = 3`: the amount of nearest neighbors considered, in order to compute σ*k^2 (read algorithm description [`uzal*cost`]@ref). If given a vector, the minimum result over all`knn ∈ KNN` is returned.
  * `L_threshold::Real = 0`: The algorithm breaks, when this threshold is exceeded by `ΔL` in an embedding cycle (set as a positive number, i.e. an absolute value of `ΔL`).
  * `α::Real = 0.05`: The significance level for obtaining the continuity statistic
  * `p::Real = 0.5`: The p-parameter for the binomial distribution used for the computation of the continuity statistic ⟨ε★⟩.
  * `max_cycles = 50`: The algorithm will stop after that many cycles no matter what.
  * `econ::Bool = false`: Economy-mode for L-statistic computation. Instead of computing L-statistics for time horizons `2:Tw`, here we only compute them for `2:2:Tw`, see description for further details.
  * `verbose = true`: Print information about the process.

## Description

The method works iteratively and gradually builds the final embedding vectors `Y`. Based on the `⟨ε★⟩`-statistic (of [`pecora`](@ref)) the algorithm picks an optimal delay value `τᵢ` for each embedding cycle `i`. For achieving that, we take the inpute time series `s`, denoted as the actual phase space trajectory `Y_actual` and compute the continuity statistic `⟨ε★⟩`.

1. Each local maxima in `⟨ε★⟩` is used for constructing a candidate embedding trajectory `Y_trial` with a delay corresponding to that specific peak in `⟨ε★⟩`.
2. We then compute the `L`-statistic (of [`uzal_cost`](@ref)) for `Y_trial` (`L-trial`) and `Y_actual` (`L_actual`) for increasing prediction time horizons (free parameter in the `L`-statistic) and save the maximum difference `max(L-trial - L_actual)` as `ΔL` (Note that this is a negative number, since the `L`-statistic decreases with better reconstructions).
3. We pick the `τ`-value, for which `ΔL` is minimal (=maximum decrease of the overall `L`-value) and construct the actual embedding trajectory `Y_actual` (steps 1.-3. correspond to an embedding cycle).
4. We repeat steps 1.-3. with `Y_actual` as input and stop the algorithm when `ΔL` is > 0, i.e. when and additional embedding component would not lead to a lower overall L-value. `Y_actual` -> `Y`.

In case of multivariate embedding, i.e. when embedding a set of M time series (`s::StateSpaceSet`), in each embedding cycle the continuity statistic `⟨ε★⟩` gets computed for all M time series available. The optimal delay value `τ` in each embedding cycle is chosen as the peak/`τ`-value for which `ΔL` is minimal under all available peaks and under all M `⟨ε★⟩`'s. In the first embedding cycle there will be M² different `⟨ε★⟩`'s to consider, since it is not clear a priori which time series of the input should consitute the first component of the embedding vector and form `Y_actual`.

The range of considered delay values is determined in `τs` and for the nearest neighbor search we respect the Theiler window `w`. The final embedding vector is stored in `Y` (`StateSpaceSet`). The chosen delay values for each embedding cycle are stored in `τ_vals` and the according time series numbers chosen for each delay value in `τ_vals` are stored in `ts_vals`. For univariate embedding (`s::Vector`) `ts_vals` is a vector of ones of length `τ_vals`, because there is simply just one timeseries to choose from. The function also returns the `ΔLs`-values for each embedding cycle and the continuity statistic `⟨ε★⟩` as an `Array` of `Vector`s.

For distance computations the Euclidean norm is used.

[^Kraemer2021]: Kraemer, K.H., Datseris, G., Kurths, J., Kiss, I.Z., Ocampo-Espindola, Marwan, N. (2021) [A unified and automated approach to attractor reconstruction. New Journal of Physics 23(3), 033017](https://iopscience.iop.org/article/10.1088/1367-2630/abe336).
