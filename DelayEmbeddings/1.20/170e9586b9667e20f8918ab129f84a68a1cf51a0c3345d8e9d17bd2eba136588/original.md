```
optimal_traditional_de(s, method = "afnn", dmethod = "mi_min"; kwargs...) → 𝒟, τ, E
```

Produce an optimal delay embedding `𝒟` of the given timeseries `s` by using the traditional approach of first finding an optimal (and constant) delay time using [`estimate_delay`](@ref) with the given `dmethod`, and then an optimal embedding dimension, by calculating an appropriate statistic for each dimension `d ∈ 1:dmax`. Return the embedding `𝒟`, the optimal delay time `τ` (the optimal embedding dimension `d` is just `size(𝒟, 2)`) and the actual statistic `E` used to estimate optimal `d`.

Notice that `E` is a function of the embedding dimension, which ranges from 1 to `dmax`.

For calculating `E` to estimate the dimension we use the given `method` which can be:

  * `"afnn"` (default) is Cao's "Averaged False Nearest Neighbors" method[^Cao1997],   which gives a ratio of distances between nearest neighbors.
  * `"ifnn"` is the "Improved False Nearest Neighbors" from Hegger & Kantz[^Hegger1999],   which gives the fraction of false nearest neighbors.
  * `"fnn"` is Kennel's "False Nearest Neighbors" method[^Kennel1992], which gives   the number of points that cease to be "nearest neighbors" when the dimension   increases.
  * `"f1nn"` is Krakovská's "False First Nearest Neighbors" method[^Krakovská2015],   which gives the ratio of pairs of points that cease to be "nearest neighbors"   when the dimension increases.

For more details, see individual methods: [`delay_afnn`](@ref), [`delay_ifnn`](@ref), [`delay_fnn`](@ref), [`delay_f1nn`](@ref). The special keywords `` denote for which possible embedding dimensions should the statistics be computed for.

!!! warn "Careful in automated methods"
    While this method is automated if you want to be **really sure** of the results, you should directly calculate the statistic and plot its values versus the dimensions.


## Keywords

The keywords

```
τs = 1:100, dmax = 10
```

denote which delay times and embedding dimensions `ds ∈ 1:dmax` to consider when calculating optimal embedding. All remaining keywords are propagated to the low level functions:

```
fnn_thres::Real = 0.05, slope_thres::Real= 0.2, w::Int=1,
rtol=10.0, atol=2.0, τs = 1:100, metric = Euclidean(), r::Real=2.0,
stoch_thres = 0.1
```

## Description

We estimate the optimal embedding dimension based on the given delay time gained from `dmethod` as follows: For Cao's method the optimal dimension is reached, when the slope of the `E₁`-statistic (output from `"afnn"`) falls below the threshold `slope_thres` (default is .05) and the according stochastic test turns out to be false, i.e. if the `E₂`-statistic's first value is `< 1 - stoch_thres`.

For all the other methods we return the optimal embedding dimension when the corresponding FNN-statistic (output from `"ifnn"`, `"fnn"` or `"f1nn"`) falls below the fnn-threshold `fnn_thres` (Default is .05) AND the slope of the statistic falls below the threshold `slope_thres`. Note that with noise contaminated time series, one might need to adjust `fnn_thres` according to the noise level.

See also the file `test/compare_different_dimension_estimations.jl` for a comparison.

[^Cao1997]: Liangyue Cao, [Physica D, pp. 43-50 (1997)](https://www.sciencedirect.com/science/article/pii/S0167278997001188?via%3Dihub)

[^Kennel1992]: M. Kennel *et al.*, [Phys. Review A **45**(6), (1992)](https://journals.aps.org/pra/abstract/10.1103/PhysRevA.45.3403).

[^Krakovská2015]: Anna Krakovská *et al.*, [J. Complex Sys. 932750 (2015)](https://doi.org/10.1155/2015/932750)

[^Hegger1999]: Hegger & Kantz, [Improved false nearest neighbor method to detect determinism in time series data. Physical Review E 60, 4970](https://doi.org/10.1103/PhysRevE.60.4970).
