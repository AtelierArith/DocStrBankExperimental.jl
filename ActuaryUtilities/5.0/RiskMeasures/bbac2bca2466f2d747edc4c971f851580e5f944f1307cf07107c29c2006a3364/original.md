```
ProportionalHazard(y)::RiskMeasure
ProportionalHazard(y)(risk)::T (where T is the type of values sampled in risk)
```

The Proportional Hazard distortion risk measure is defined as $x^(1/y)$, where x is the cumulative distribution function (CDF) of the risk distribution and y is a positive parameter. risk can be a univariate distribution or an array of outcomes. ProportionalHazard(y) returns a functor which can then be called on a risk distribution.

## Examples

```julia-repl
julia> ProportionalHazard(2)(rand(1000))
0.6659603556774121

julia> rm = ProportionalHazard(2)
ProportionalHazard{Int64}(2)

julia> rm(rand(1000))
0.6710587338367799
```
