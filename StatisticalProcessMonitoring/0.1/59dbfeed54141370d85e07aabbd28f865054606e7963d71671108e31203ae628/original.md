```
NEWMA(λ::Float64, g::F, dat::FunctionalData)
```

Construct a NEWMA control chart by calculating the standard errors for a functional regression model.

# Arguments

  * `λ::Float64`: The EWMA smoothing constant. Must be between 0 and 1.
  * `g::F`: The estimated regression function object. Must have a method of signature `predict(g::F, x::AbstractVector)`.
  * `dat::FunctionalData`: A `FunctionalData` object containing observations of the regression curves.
  * `Ej::Vector{Float64}`: The current smoothed observations.

# Returns

The constructed NEWMA control chart.

# Examples

```
using Loess
xs = 10 .* rand(100)
ys = sin.(xs) .+ rand(100)
g = loess(xs, ys)
dat = FunctionalData(xs, ys)
NEWMA(0.2, g, dat)
```
