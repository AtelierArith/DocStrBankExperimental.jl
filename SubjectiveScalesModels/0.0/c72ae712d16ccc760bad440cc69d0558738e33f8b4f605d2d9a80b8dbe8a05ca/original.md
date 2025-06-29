```
BetaPhi2(μ, ϕ)
```

Construct a Beta distribution with parameters mean `μ` and precision `ϕ`. It is defined as `Beta(μ * 2ϕ, (1 - μ) * 2ϕ)`.

# Arguments

  * `μ`: Location parameter (range: $]0, 1[$).
  * `ϕ`: Precision parameter (must be $> 0$).

# Details

*Beta Phi2* is a variant of the traditional *Mu-Phi* location-precision parametrization.  The modification - scaling ϕ by a factor of 1/2 - creates in a Beta distribution in which, when μ is at its center (i.e., 0.5), a parameter ϕ equal to 1 results in a flat prior (i.e., $Beta(1, 1)$). It is useful to set priors for ϕ on the log scale in regression models, so that a prior of $Normal(0, 1)$ assigns the most probability on a flat distribution (ϕ=1).

![](https://github.com/DominiqueMakowski/SubjectiveScalesModels.jl/blob/main/docs/img/animation_BetaPhi2.gif?raw=true)

The red area shows the region where the distribution assigns the highest probability to extreme values (towards 0 and/or 1). The blue area shows the region where the distribution is "convex" and peaks within the $]0, 1[$ interval.

# Examples

```jldoctest
julia> BetaPhi2(0.5, 1)
BetaPhi2{Float64}(μ=0.5, ϕ=1.0)
```
