```
delay_afnn(s::AbstractVector, τ:Int, ds = 2:6; metric=Euclidean(), w = 0) → E₁
```

Compute the parameter E₁ of Cao's "averaged false nearest neighbors" method for determining the minimum embedding dimension of the time series `s`, with a sequence of `τ`-delayed temporal neighbors.

## Description

Given the scalar timeseries `s` and the embedding delay `τ` compute the values of `E₁` for each embedding dimension `d ∈ ds`, according to Cao's Method (eq. 3 of[^Cao1997]).

This quantity is a ratio of the averaged distances between the nearest neighbors of the reconstructed time series, which quantifies the increment of those distances when the embedding dimension changes from `d` to `d+1`.

Return the vector of all computed `E₁`s. To estimate a good value for `d` from this, find `d` for which the value `E₁` saturates at some value around 1.

*Note: This method does not work for datasets with perfectly periodic signals.*

`w` is the [Theiler window](@ref).

See also: [`optimal_traditional_de`](@ref) and [`stochastic_indicator`](@ref).
