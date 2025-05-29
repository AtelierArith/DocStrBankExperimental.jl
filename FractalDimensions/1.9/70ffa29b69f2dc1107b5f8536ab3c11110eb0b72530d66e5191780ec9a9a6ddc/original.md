```
estimate_gev_parameters(X::AbstractVector{<:Real}, θ::Real)
```

Estimate and return the parameters `σ, μ` of a Generalized Extreme Value distribution fit to `X` (which typically is the collected block maxima of the log distances of a state space set), assuming that the parameter `ξ` is 0, and that the extremal index θ is a known constant, and can be estimated through the function `extremal_index_sueveges`. The estimators through the method of moments are given by     σ = √((̄x²-̄x^2)/(π^2/6))     μ = ̄x - σ(log(θ) + γ) where γ is the constant of Euler-Mascheroni.
