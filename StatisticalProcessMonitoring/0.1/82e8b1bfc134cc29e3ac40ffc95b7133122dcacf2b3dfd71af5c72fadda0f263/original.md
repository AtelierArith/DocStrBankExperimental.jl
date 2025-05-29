```
ThompsonSampling <: AbstractSampling
```

Type representing the Thompson Sampling method.

# Fields

  * `β::Float64`: A parameter regulating the concentration of the `Dirichlet` distribution for Thompson sampling.

# Examples

```julia
ts = ThompsonSampling(2.0)
```
