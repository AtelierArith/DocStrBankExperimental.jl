```
initialize(::Type{<:SimpleScaling}, data::IDFdata, d₀::Real)
```

Initialize a vector of parameters for the SimpleScaling marginal model with reference duration d₀, adapted to the data. The initialization is done by fitting a Gumbel distribution independently for each duration in the data and then estimating the scaling relationship by     regression over μ and σ. ξ is initialized at 0 as a default.
