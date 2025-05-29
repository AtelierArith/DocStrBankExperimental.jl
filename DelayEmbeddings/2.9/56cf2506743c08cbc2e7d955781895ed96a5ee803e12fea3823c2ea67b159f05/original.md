```
pecora(s, τs, js; kwargs...) → ⟨ε★⟩, ⟨Γ⟩
```

Compute the (average) continuity statistic `⟨ε★⟩` and undersampling statistic `⟨Γ⟩` according to Pecora et al.[^Pecoral2007] (A unified approach to attractor reconstruction), for a given input `s` (timeseries or `StateSpaceSet`) and input generalized embedding defined by `(τs, js)`, according to [`genembed`](@ref). The continuity statistic represents functional independence between the components of the existing embedding and one additional timeseries. The returned results are *matrices* with size `T`x`J`.

## Keyword arguments

  * `delays = 0:50`: Possible time delay values `delays` (in sampling time units). For each of the `τ`'s in `delays` the continuity-statistic `⟨ε★⟩` gets computed. If `undersampling = true` (see further down), also the undersampling statistic `⟨Γ⟩` gets returned for all considered delay values.
  * `J = 1:dimension(s)`: calculate for all timeseries indices in `J`. If input `s` is a timeseries, this is always just 1.
  * `samplesize::Real = 0.1`: determine the fraction of all phase space points (=`length(s)`) to be considered (fiducial points v) to average ε★ to produce `⟨ε★⟩, ⟨Γ⟩`
  * `K::Int = 13`: the amount of nearest neighbors in the δ-ball (read algorithm description). Must be at least 8 (in order to gurantee a valid statistic). `⟨ε★⟩` is computed taking the minimum result over all `k ∈ K`.
  * `metric = Chebyshev()`: metrix with which to find nearest neigbhors in the input embedding (ℝᵈ space, `d = length(τs)`).
  * `w = 1`: Theiler window (neighbors in time with index `w` close to the point, that are excluded from being true neighbors). `w=0` means to exclude only the point itself, and no temporal neighbors.
  * `undersampling = false` : whether to calculate the undersampling statistic or not (if not, zeros are returned for `⟨Γ⟩`). Calculating `⟨Γ⟩` is thousands of times slower than `⟨ε★⟩`.
  * `db::Int = 100`: Amount of bins used into calculating the histograms of each timeseries (for the undersampling statistic).
  * `α::Real = 0.05`: The significance level for obtaining the continuity statistic
  * `p::Real = 0.5`: The p-parameter for the binomial distribution used for the computation of the continuity statistic.

## Description

Notice that the full algorithm is too large to discuss here, and is written in detail (several pages!) in the source code of `pecora`.

[^Pecora2007]: Pecora, L. M., Moniz, L., Nichols, J., & Carroll, T. L. (2007). [A unified approach to attractor reconstruction. Chaos 17(1)](https://doi.org/10.1063/1.2430294).
