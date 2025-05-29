```julia
struct CategoricalFactor <: Distributions.Distribution{Distributions.Univariate, Distributions.Discrete}
```

  * `values::Vector`
  * `distribution::Distributions.DiscreteUniform`

A simple wrapper for a `DiscreteUniform` distribution over non-numerical arrays.
