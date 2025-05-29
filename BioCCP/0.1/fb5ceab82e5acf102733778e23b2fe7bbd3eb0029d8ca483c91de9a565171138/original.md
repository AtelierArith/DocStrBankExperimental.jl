```
prob_occurrence_module(pᵢ, t::Integer, r, k::Integer)
```

Calculates probability that specific module with module probability `pᵢ`  has occurred `k` times after collecting `t` designs.

Sampling processes of individual modules are assumed to be independent Poisson processes.

  * `pᵢ`: module probability
  * `t`: sample size/number of designs
  * `k`: number of occurrence

References:

  * Boneh, A., & Hofri, M. (1997). The coupon-collector problem revisited—a survey of engineering problems and computational methods. Stochastic Models, 13(1), 39-66.

## Examples

```julia-repl
julia> pᵢ = 0.005
julia> t = 500
julia> k = 2
julia> r = 1
julia> prob_occurrence_module(pᵢ, t, r, k)
0.25651562069968376
```
