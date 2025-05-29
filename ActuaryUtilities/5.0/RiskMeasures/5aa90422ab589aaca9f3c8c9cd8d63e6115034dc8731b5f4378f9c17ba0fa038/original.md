```
WangTransform(α)::RiskMeasure
WangTransform(α)(risk)::T (where T is the type of values sampled in risk)
```

The Wang Transform is a distortion risk measure that transforms the cumulative distribution function (CDF) of the risk distribution using a normal distribution with mean Φ⁻¹(α) and standard deviation 1. risk can be a univariate distribution or an array of outcomes.

WangTransform(α) returns a functor which can then be called on a risk distribution.

## Parameters

  * α: [0,1.0]

In the literature, sometimes λ is used where $\lambda = \Phi^{-1}(\alpha)$.

## Examples

```julia-repl
julia> WangTransform(0.95)(rand(1000))
0.8799465543360105

julia> rm = WangTransform(0.95)
WangTransform{Float64}(0.95)

julia> rm(rand(1000))
0.8892245759705852
```

## References

  * "A Risk Measure That Goes Beyond Coherence", Shaun S. Wang, 2002
