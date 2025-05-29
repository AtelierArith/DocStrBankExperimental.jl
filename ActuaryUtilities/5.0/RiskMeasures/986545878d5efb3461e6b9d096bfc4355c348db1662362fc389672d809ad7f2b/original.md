```
CTE(α)::RiskMeasure
CTE(α)(risk)::T (where T is the type of values sampled in risk)
```

The Conditional Tail Expectation (CTE) at level α is the expected value of the risk distribution above the αth quantile. `risk` can be a univariate distribution or an array of outcomes. Assumes more positive values are higher risk measures, so a higher p will return a more positive number.

CTE(α) returns a functor which can then be called on a risk distribution.

## Parameters

  * α: [0,1.0)

## Examples

```julia-repl
julia> CTE(0.95)(rand(1000))
0.9766218612020593

julia> rm = CTE(0.95)
CTE{Float64}(0.95)

julia> rm(rand(1000))
0.9739835010268733
```
