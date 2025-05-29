```
 VaR(α)::RiskMeasure
 VaR(α)(risk)::T (where T is the type of values sampled in `risk`)
```

The `α`th quantile of the `risk` distribution is the Value at Risk, or αth quantile. `risk` can be a univariate distribution or an array of outcomes. Assumes more positive values are higher risk measures, so a higher p will return a more positive number. For a discrete risk, the VaR returned is the first value above the αth percentile.

`VaR(α)` returns a functor which can then be called on a risk distribution.

## Parameters

  * α: [0,1.0)

## Examples

```julia-repl
julia> VaR(0.95)(rand(1000))
0.9561843082268024

julia> rm = VaR(0.95)
VaR{Float64}(0.95)

julia> rm(rand(1000))
0.9597070153670079
```
