```
SubSetInfinityAdaptive(n::Integer, target::Float64, levels::Integer, Na::Integer, λ::Real, s::Real)
```

Implementation of: Papaioannou, Iason, et al. "MCMC algorithms for subset simulation." Probabilistic Engineering Mechanics 41 (2015): 89-103

Defines the properties of a Subset-∞ adaptive where `n` are the number of samples per level, `target` is the target probability of failure at each level, `levels` is the maximum number of levels, `λ` (λ = 1 recommended) is the initial scaling parameter, and `Na` is the number simulations that will be run before `λ` is updated. Note that Na must be a multiple of n * target: `mod(ceil(n * target), Na) == 0)`. The initial variance of the proposal distribution is `s`.

Idea behind this algorithm is to adaptively select the correlation parameter of `s` at each intermediate level, by simulating a subset Na of the chains (which must be choosen without replacement at random) and modifying the acceptance rate towards the optimal αstar = 0.44

# Constructors

  * `SubSetInfinityAdaptive(n::Integer, target::Float64, levels::Integer, Na::Integer)`   (default: λ = s = 1)
  * `SubSetInfinityAdaptive(n::Integer, target::Float64, levels::Integer, Na::Integer, λ::Real)` (λ = s)
  * `SubSetInfinityAdaptive(n::Integer, target::Float64, levels::Integer, Na::Integer, λ::Real, s::Real)`

# Note

The following constructors will run the same number of samples, but SubSetInfinityAdaptive will update `s` after each chain:

  * `SubSetInfinityAdaptive(400, 0.1, 10, 40)`
  * `SubSetInfinity(400, 0.1, 10, 0.5)`

# Examples

```jldoctest
julia> SubSetInfinityAdaptive(200, 0.1, 10, 2)
SubSetInfinityAdaptive(200, 0.1, 10, 2, 1, 1)
```

# References

[papaioannou2015mcmc](@cite)

[chan2022adaptive](@cite)
