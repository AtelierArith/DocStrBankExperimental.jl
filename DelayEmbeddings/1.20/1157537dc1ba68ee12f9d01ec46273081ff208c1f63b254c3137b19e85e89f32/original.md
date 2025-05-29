```
estimate_dimension(s::AbstractVector, τ::Int, γs = 1:5, method = "afnn"; kwargs...)
```

Compute a quantity that can estimate an optimal amount of temporal neighbors `γ` to be used in [`reconstruct`](@ref) or [`embed`](@ref).

## Description

Given the scalar timeseries `s` and the embedding delay `τ` compute a quantity for each `γ ∈ γs` based on the "nearest neighbors" in the embedded time series.

The quantity that is calculated depends on the algorithm defined by the string `method`:

  * `"afnn"` (default) is Cao's "Averaged False Nearest Neighbors" method[^Cao1997], which   gives a ratio of distances between nearest neighbors. This ratio saturates   around `1.0` near the optimal value of `γ` (see [`afnn`](@ref)).
  * `"fnn"` is Kennel's "False Nearest Neighbors" method[^Kennel1992], which gives the   number of points that cease to be "nearest neighbors" when the dimension   increases. This number drops down to zero near the optimal value of `γ`.   This method accepts the keyword arguments `rtol` and `atol`, which stand   for the "tolerances" required by Kennel's algorithm (see [`fnn`](@ref)).
  * `"f1nn"` is Krakovská's "False First Nearest Neighbors" method[^Krakovská2015], which   gives the ratio of pairs of points that cease to be "nearest neighbors"   when the dimension increases. This number drops down to zero near the   optimal value of `γ` (see [`f1nn`](@ref)). This is the worse method of all.

`"afnn"` and `"f1nn"` also support the `metric` keyword, which can be any of `Cityblock(), Euclidean(), Chebyshev()`. This metric is used both for computing the nearest neighbors (`KDTree`s) as well as the distances necessary for Cao's method (eqs. (2, 3) of [1]). Defaults to `Euclidean()` (note that [1] used `Chebyshev`).

Please be aware that in **DynamicalSystems.jl** `γ` stands for the amount of temporal neighbors and not the embedding dimension (`D = γ + 1`, see also [`embed`](@ref)).

[^Cao1997]: Liangyue Cao, [Physica D, pp. 43-50 (1997)](https://www.sciencedirect.com/science/article/pii/S0167278997001188?via%3Dihub)

[^Kennel1992]: M. Kennel *et al.*, [Phys. Review A **45**(6), (1992)](https://journals.aps.org/pra/abstract/10.1103/PhysRevA.45.3403).

[^Krakovská2015]: Anna Krakovská *et al.*, [J. Complex Sys. 932750 (2015)](https://doi.org/10.1155/2015/932750)
