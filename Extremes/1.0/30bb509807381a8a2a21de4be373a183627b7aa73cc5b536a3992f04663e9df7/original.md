```
gevfit()
```

Estimate the GEV parameters by maximum likelihood.

# Implementation

The function uses Nelder-Mead solver implemented in the [Optim.jl](https://github.com/JuliaNLSolvers/Optim.jl) package to find the point where the log-likelihood is maximal.

The GEV parameters can be modeled as function of covariates as follows:

$$
μ = X₁ × β₁,
$$

$$
ϕ = X₂ × β₂,
$$

$$
ξ = X₃ × β₃.
$$

The covariates are standardized before estimating the parameters to help fit the  model. They are transformed back on their original scales before returning the  fitted model.

See also [`gevfit`](@ref) for the other methods, [`gevfitpwm`](@ref), [`gevfitbayes`](@ref) and [`BlockMaxima`](@ref).
