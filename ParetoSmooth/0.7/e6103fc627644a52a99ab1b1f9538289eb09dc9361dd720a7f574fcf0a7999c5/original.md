```
psis!(
    is_ratios::AbstractVector{<:Real}; 
    tail_length::Integer, log_weights::Bool=true
) -> Real
```

Do PSIS on a single vector, smoothing its tail values *in place* before returning the  estimated shape constant for the `pareto_k` distribution. This *does not* normalize the  log-weights.

# Arguments

  * `is_ratios::AbstractVector{<:Real}`: A vector of importance sampling ratios, scaled to have a maximum of 1.
  * `r_eff::AbstractVector{<:Real}`: The relative effective sample size, used to calculate the effective sample size. See [rel_eff]@ref for more information.
  * `log_weights::Bool`: A boolean indicating whether the input vector is a vector of log ratios, rather than raw importance sampling ratios.

# Returns

  * `Real`: ξ, the shape parameter for the GPD. Bigger numbers indicate thicker tails.

# Notes

Unlike the methods for arrays, `psis!` performs no checks to make sure the input values are  valid.
