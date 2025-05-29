```
gpfit(...)
```

Estimate the GP parameters by maximum likelihood.

Data provided must be the exceedances above the threshold, *i.e.* the data above the threshold minus the threshold.

# Implementation

The function uses Nelder-Mead solver implemented in the [Optim.jl](https://github.com/JuliaNLSolvers/Optim.jl) package to find the point where the log-likelihood is maximal.

The GP parameters can be modeled as function of covariates as follows:

$$
ϕ = X₂ × β₂,
$$

$$
ξ = X₃ × β₃.
$$

The covariates are standardized before estimating the parameters to help fit the  model. They are transformed back on their original scales before returning the  fitted model.

See also [`gpfit`](@ref) for the other methods, [`gpfitpwm`](@ref), [`gpfitbayes`](@ref) and [`ThresholdExceedance`](@ref).
