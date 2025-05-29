```
GLM.dispersion_parameter(D)
```

Does distribution `D` have a separate dispersion parameter, ϕ?

Returns `false` for the `Bernoulli`, `Binomial` and `Poisson` distributions, `true` otherwise.

# Examples

```jldoctest; setup = :(using GLM)
julia> show(GLM.dispersion_parameter(Normal()))
true
julia> show(GLM.dispersion_parameter(Bernoulli()))
false
```
